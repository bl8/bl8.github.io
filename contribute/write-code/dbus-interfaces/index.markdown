---
layout: page
title: DBus Interfaces
show-sidebar: true
sidebar-group: none
---

Banshee exposes a lot of functionality through D-Bus interfaces, which you can use to make you own software interact with Banshee.

In addition to the interfaces listed below, Banshee also supports the [MPRIS D-Bus Interface Specification](http://mpris.org), which provides a common programmatic API for controlling media players.

#### [Core/Banshee.Core/Banshee.Collection/ITrackInfo.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Core/Banshee.Collection/ITrackInfo.cs)

{% highlight c# %}
[Interface("org.bansheeproject.Banshee.Tracks.Track")]
public interface ITrackInfo : IBasicTrackInfo
{
    string DisplayArtistName { get; }
    string DisplayAlbumTitle { get; }
    string DisplayTrackTitle { get; }
    string DisplayGenre { get; }
    
    int TrackNumber { get; }
    int TrackCount { get; }
    int Year { get; }
    int Rating { get; }
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.PlaybackController/IPlaybackControllerService.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.PlaybackController/IPlaybackControllerService.cs)

{% highlight c# %}
public delegate void PlaybackControllerStoppedHandler ();

[Interface ("org.bansheeproject.Banshee.PlaybackController")]
public interface IPlaybackControllerService : IDBusExportable
{
    // FIXME: IPlaybackControllerExportable : IPlaybackController
    // but DBus-Sharp has a design flaw where it only exports 
    // members of the top level interface where the [Interface] 
    // attribute is applied
    
    event PlaybackControllerStoppedHandler Stopped;
    
    void First ();
    void Next (bool restart);
    void Previous (bool restart);
    
    PlaybackShuffleMode ShuffleMode { get; set; }
    PlaybackRepeatMode RepeatMode { get; set; }
    bool StopWhenFinished { get; set; }
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.Collection.Indexer/ICollectionIndexer.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.Collection.Indexer/ICollectionIndexer.cs)

{% highlight c# %}
public delegate void SaveToXmlFinishedHandler (bool success, string path);

[Interface ("org.bansheeproject.CollectionIndexer.Indexer")]
public interface ICollectionIndexer : IService, IDBusExportable
{
    event Hyena.Action IndexingFinished;
    event SaveToXmlFinishedHandler SaveToXmlFinished;
    
    void Index ();
    void Dispose ();
    
    void SetExportFields (string [] fields);
    
    int GetModelCounts ();
    int GetModelResultsCount (int modelIndex);
    IDictionary<string, object> GetResult (int modelIndex, int itemIndex);
    
    void SaveToXml (string path);
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.Collection.Indexer/IIndexerClient.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.Collection.Indexer/IIndexerClient.cs)

{% highlight c# %}
[Interface ("org.bansheeproject.CollectionIndexer.Client")]
public interface IIndexerClient : IDBusExportable
{
    void Hello ();
    void RebootWhenFinished (string [] args);
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.Collection.Indexer/ICollectionIndexerService.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.Collection.Indexer/ICollectionIndexerService.cs)

{% highlight c# %}
[Interface ("org.bansheeproject.CollectionIndexer.Service")]
public interface ICollectionIndexerService : IService, IDBusExportable
{
    event Hyena.Action CollectionChanged;
    event Hyena.Action CleanupAndShutdown;
    
    void Hello ();
    void Shutdown ();
    ObjectPath CreateIndexer ();
    string [] GetAvailableExportFields ();
    bool HasCollectionChanged (int count, long time);
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.MediaEngine/IPlayerEngineService.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.MediaEngine/IPlayerEngineService.cs)

{% highlight c# %}
[Interface("org.bansheeproject.Banshee.PlayerEngine")]
public interface IPlayerEngineService : IDBusExportable
{
    event DBusPlayerEventHandler EventChanged;
    event DBusPlayerStateHandler StateChanged;

    void Open (string uri);
    
    void Close ();
    void Pause ();
    void Play ();
    void TogglePlaying ();
    
    IDictionary<string, object> CurrentTrack { get; }
    string CurrentUri { get; }
    
    string CurrentState { get; }
    string LastState { get; }

    ushort Volume { get; set; }
    uint Position { get; set; }
    bool CanSeek { get; }
    bool CanPause { get; }
    uint Length { get; }
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.Collection/IExportableModel.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.Collection/IExportableModel.cs)

{% highlight c# %}
[Interface("org.bansheeproject.Banshee.CollectionModel")]
public interface IExportableModel
{
    int GetLength();
    IDictionary<string, object> GetMetadata(int index);
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.ServiceStack/DBusCommandService.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.ServiceStack/DBusCommandService.cs)

{% highlight c# %}
public delegate void DBusCommandHandler (string argument, object value, bool isFile);

[Interface ("org.bansheeproject.Banshee.CommandService")]
public class DBusCommandService : MarshalByRefObject, IDBusExportable
{
    public event DBusCommandHandler ArgumentPushed;
    
    public DBusCommandService ()
    {
    }
    
    public void PushArgument (string argument, object value)
    {
        OnArgumentPushed (argument, value, false);
    }
    
    public void PushFile (string file)
    {
        OnArgumentPushed (file, String.Empty, true);
    }
    
    private void OnArgumentPushed (string argument, object value, bool isFile)
    {
        DBusCommandHandler handler = ArgumentPushed;
        if (handler != null) {
            handler (argument, value, isFile);
        }
    }
    
    IDBusExportable IDBusExportable.Parent {
        get { return null; }
    }
    
    string IService.ServiceName {
        get { return "DBusCommandService"; }
    }
}
{% endhighlight%}

#### [Core/Banshee.Services/Banshee.Sources/ISourceManager.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.Services/Banshee.Sources/ISourceManager.cs)

{% highlight c# %}
[Interface("org.bansheeproject.Banshee.SourceManager")]
public interface ISourceManager : IDBusExportable
{
    //event SourceEventHandler SourceUpdated; 
    ISource ActiveSource { get; set; }
    ISource DefaultSource { get; }
    string [] Sources { get; }
}
{% endhighlight%}

#### [Core/Banshee.ThickClient/Banshee.Gui/IClientWindow.cs](http://git.gnome.org/cgit/banshee/tree/src/Core/Banshee.ThickClient/Banshee.Gui/IClientWindow.cs)

{% highlight c# %}
[Interface ("org.bansheeproject.Banshee.ClientWindow")]
public interface IClientWindow : IDBusExportable
{
    void Present ();
    void Hide ();
}
{% endhighlight%}
