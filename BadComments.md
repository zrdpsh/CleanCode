import java.util.ArrayList;

```
public class MusicOrganizer
{
```
~~// An ArrayList for storing music tracks.~~ - 7. Комментарий избыточен.
```
    private ArrayList<Track> tracks;
```
~~// A player for the music tracks.~~ - 7. Комментарий избыточен.
```
    private MusicPlayer player;

    // A reader that can read music files and load them as tracks.

    private TrackReader reader;
```

```
public MusicOrganizer()
{
    tracks = new ArrayList<Track>();
    player = new MusicPlayer();
    reader = new TrackReader();
    readLibrary("audio");
    System.out.println("Music library loaded. " + getNumberOfTracks() + " tracks.");
    System.out.println();
}
```




  
~~/**~~
~~* Add a track file to the collection.
 */~~ - 7. Комментарий избыточен.

```   
public void addFile(String filename)
{
    tracks.add(new Track(filename));
}
```




~~/**~~
~~* Add a track to the collection.
 */~~ - 12. Можно использовать имя функции
```
~~public void addTrack(Track track)~~ 
public void addTrackToPlaylist(Track track)
{
    tracks.add(track);
}
```




~~/**~~
~~* Play a track in the collection.
 */~~ - 7. Комментарий избыточен.
```
public void playTrack(int index)
{
    if(indexIsValid(index)) {
        Track track = tracks.get(index);
        player.startPlaying(track.getFilename());
        System.out.println("Now playing: " + track.getArtist() + " - " + track.getTitle());
    }
}
```




~~/**~~
~~* Return the number of tracks in the collection.
 */~~ - 7. Комментарий избыточен.
```
public int getNumberOfTracks()
{
    return tracks.size();
}
```




   
~~/**~~
~~* List a track from the collection.
 */~~ - 7. Комментарий избыточен.
``` 
public void listTrack(int index)
{
    System.out.print("Track " + index + ": ");
    Track track = tracks.get(index);
    System.out.println(track.getDetails());
}
```




~/**
~~* Show a list of all the tracks in the collection.
 */~~ - 7. Комментарий избыточен.
``` 
public void listAllTracks()
{
    System.out.println("Track listing: ");

    for(Track track : tracks) {
        System.out.println(track.getDetails());
    }
    System.out.println();
}
```




~~/**~~
~~* List all tracks by the given artist.
 */~~ - 7. Комментарий избыточен.
```
public void listByArtist(String artist)
{
    for(Track track : tracks) {
        if(track.getArtist().contains(artist)) {
            System.out.println(track.getDetails());
        }
    }
}
``` 




~~/**~~
~~* Remove a track from the collection.
 */~~ - 7. Комментарий избыточен.
```
public void removeTrack(int index)
{
    if(indexValid(index)) {
        tracks.remove(index);
    }
}
```




~~/**~~
~~* Play the first track in the collection, if there is one.
 */~~ - 7. Комментарий избыточен.
``` 
public void playFirst()
{
    if(tracks.size() > 0) {
        player.startPlaying(tracks.get(0).getFilename());
    }
}
```





~~/**~~
~~* Stop the player.
 */~~ - 7. Комментарий избыточен.
``` 
public void stopPlaying()
{
    player.stop();
}
```





~~/**~~
~~* Determine whether the given index is valid for the collection.~~
~~* Print an error message if it is not.~~
~~*/~~- - 12. Можно использовать имя функции
```
private boolean indexIsValid(int index)
{
```
~~// The return value.~~
~~// Set according to whether the index is valid or not.~~ - 7. Комментарий избыточен.
```
    boolean valid;
    
    if(index < 0) {
        System.out.println("Index cannot be negative: " + index);
        valid = false;
    }
    else if(index >= tracks.size()) {
        System.out.println("Index is too large: " + index);
        valid = false;
    }
    else {
        valid = true;
    }
    return valid;
}
```




```
// Read complete folder from the disk - прояснение
private void readLibrary(String folderName)
{
    ArrayList<Track> tempTracks = reader.readTracks(folderName, ".mp3");
```
~~// Put all thetracks into the organizer.~~ - 7. Комментарий избыточен.
```
    for(Track track : tempTracks) {
        addTrack(track);
    }
}
}
```











