# FunctionalProgramming
My simple attempt into functional programming with JavaScript

```javascript
var playList = [
    {
        artist: 'Usher',
        songs: [
            {
                trackId: 1,
                trackName: 'DJ Got Us In Love Again'
            },
            {
                trackId: 2,
                trackName: 'Yeah'
            },
            {
                trackId: 3,
                trackName: 'I Don\'t mind'
            },
            {
                trackId: 4,
                trackName: 'Burn'
            },
            {
                trackId: 5,
                trackName: 'You Got It Bad'
            }
        ]
    },
    {
        artist: 'Eminem',
        songs: [
            {
                trackId: 1,
                trackName: 'Lose Yourself'
            },
            {
                trackId: 2,
                trackName: 'The Way I Am'
            },
            {
                trackId: 3,
                trackName: 'Not Afraid'
            }
        ]
    }
];

var playTrack = function(songs) {
    var count = songs.length;
    var trackNo = Math.floor(Math.random() * count);
    return songs[trackNo].trackName;
};

var mapArtist = function(artistName, list) {
    if (list.artist.indexOf(artistName)) {
        return playTrack(list.songs);
    }
};

var play = function(track) {
    return 'Now playing ' + track;
};

var loadPlaylist = function(playlist, fn) {
    return function(artistName) {
        return playlist
            .map(mapArtist.bind(null, artistName))
            .reduce(fn);
    };
};

var rnb = loadPlaylist(playList, play);

console.log(rnb('Eminem'));
```
