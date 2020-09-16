# react-native-gif-search
> An easy-to-use, highly customizable react-native package for searching and selecting a gif using the Giphy API.

<p align="center">
  <a href="https://www.npmjs.com/package/react-native-gif-search"><img alt="npm downloads" src="https://img.shields.io/npm/dm/react-native-gif-search.svg"/></a>
  <a href="https://www.npmjs.com/package/react-native-gif-search"><img alt="npm version" src="https://badge.fury.io/js/react-native-gif-search.svg"/></a>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search%20screenshot%201.jpg" width="250" title="react-native-gif-searc screenshot 1">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search-with-giphy-logo.gif" width="250" title="react-native-gif-search-with-giphy-logo">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search-without-giphy-logo.gif" width="250" title="react-native-gif-search-without-giphy-logo">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search%20screenshot%202.jpg" width="757" title="react-native-gif-searc screenshot 2">
</p>


This package allows you to present a searchable list of gifs to the user, from which the user can select the desired gif. In the beginning and when the search term is empty, a list of **trending gifs** is shown. You can use this component inside a chat screen, for posts, comments or wherever else you need. It uses the [Giphy API](https://developers.giphy.com/) so you need to create an account and obtain an API key which is free and easy. [This article](https://medium.com/just-ship-it-coding/integrating-giphy-api-in-react-native-8dc55dc172c8) was helpful for creating this package and has instrauctions on how to get an API key.

If you wish to **publish your app** and go from development to production you need to upgrade the API key. To do so, you must verify that you have used the Giphy attribution marks (Giphy logos) in your app, by providing screenshots and videos from your app. The verification process can take up to 3 days. The `react-native-gif-search` package can help you with this too, because it has a property for adding dark or white version of the powered by Giphy logo (`developmentMode={false}`) as you can see in the preview above.

## Installation

```
npm install react-native-gif-search --save
```

### Android

In your project's folder go to file `android/app/build.gradle` and inside dependencies block add these lines:
```
implementation 'com.facebook.fresco:fresco:2.0.0'
implementation 'com.facebook.fresco:animated-gif:2.0.0'
```

## New features

- v1.0.7
  - **numColumns**: Displaying gifs in grid view with specific number of columns. See [Properties](#properties) section below. Credits to [anthlasserre](https://github.com/anthlasserre) for suggesting and helping add this feature.
  - **onGifLongPress**: Function for when the user long presses on a link. This can be used to show a bigger preview. See [Properties](#properties) section below.


## Usage
### Import

```
import {GifSearch} from 'react-native-gif-search'
```

### Minimal example

  
```
<GifSearch
  giphyApiKey={YOUR_GIPHY_API_KEY}
  onGifSelected={(gif_url)=>{alert(gif_url)}}
/>
```

<p align="center">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search%20screenshot%203.jpg" width="300" title="react-native-gif-searc screenshot 3">
</p>


### Bigger example
```
<GifSearch
  giphyApiKey={YOUR_GIPHY_API_KEY}
  gifsToLoad={10}
  maxGifsToLoad={25}
  style={{backgroundColor: 'white', borderWidth: 3, borderRadius: 10}}
  textInputStyle={{fontWeight: 'bold', color: 'black'}}
  gifListStyle={{height:320}}
  gifStyle={{height:160}}
  loadingSpinnerColor={'black'}
  placeholderTextColor={'grey'}
  placeholderText={'Search'}
  darkGiphyLogo={true}
  onGifSelected={(gif_url) => {console.log(gif_url)}}
  visible={this.state.visible}
  onBackPressed={() => {this.setState({visible: false})}}
  developmentMode={false}
  horizontal={false}
  showScrollBar={false}
  onError={(error) => {console.log(error)}}
/>
```

<p align="center">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search%20screenshot%204.jpg" width="250" title="react-native-gif-searc screenshot 4">
</p>

### Multiple columns example
```
<GifSearch
  giphyApiKey={YOUR_GIPHY_API_KEY}
  onGifSelected={(gif_url)=>{alert(gif_url)}}
  style={{backgroundColor: '#9fd4ab', height:300}}
  textInputStyle={{fontWeight: 'bold', color: 'black'}}
  loadingSpinnerColor={'black'}
  placeholderTextColor={'grey'}
  darkGiphyLogo={true}
  numColumns={5}
  developmentMode={false}
  showScrollBar={false}
/>
```

<p align="center">
  <img src="https://raw.githubusercontent.com/Thanasis1101/react-native-gif-search/master/Preview/react-native-gif-search%20screenshot%205.jpg" width="250" title="react-native-gif-searc screenshot 5">
</p>

You can see a full example project in the [example](example/) folder and more specifically in the [App.js](example/App.js) file.

# Properties

| Property name | Required | Explanation | Default |
| --- | --- | --- | --- |
| `giphyApiKey` | Yes | The Giphy API key you obtained (see step 1 [here](https://medium.com/just-ship-it-coding/integrating-giphy-api-in-react-native-8dc55dc172c8)) |  |
| `onGifSelected` | Yes | Function to be called when user clicked on a gif. The parameter of this function is a string with the url of the selected gif in better quality | |
| `gifsToLoad` | No | How many gifs to load in the beginning and every time the user reaches the scroll end | `15` |
| `maxGifsToLoad` | No | On how many gifs to stop loading more gifs | `60` |
| `developmentMode` | No | Giphy logo appears on top right corner, if set to false (this is required by Giphy when publishing your app) | `true` |
| `darkGiphyLogo` | No | Used with `developmentMode={false}` shows the gray Giphy logo if set to true, or the white Giphy logo if set to false | `false` |
| `placeholderText` | No | The text for when there is no search term | `'Search GIF'` |
| `visible` | No | Can be used for toggling the view for the gif selection (e.g. open on button press) | `true` |
| `onBackPressed` | No | Function for when the device's back button is pressed. Used with `visible={this.state.visible}` for closing the gif selection when back button is pressed. If not set then default action is taken. If set then default action is ignored while gif selection is visible. Recommended usage: `onBackPressed={() => {this.setState({visible: false})}}` | |
| `onError` | No | Function to be called when an error occures, e.g. no internet connection | |
| `horizontal` | No | Set the orientation of the list with the gifs. Horizontal if true, vertical if false  | `true` |
| `style` | No | The component's style property (e.g. `style={{backgroundColor: 'yellow', borderRadius: 5}}`) | |
| `textInputStyle` | No | The style of the search text input | |
| `gifStyle` | No | The style of the gif inside the list | |
| `gifListStyle` | No | The style for the FlatList used for displaying the gifs | |
| `loadingSpinnerColor` | No | The color of the loading spinner | `'white'` |
| `placeholderTextColor` | No | The color of the placeholder for the search text input | `'grey'` |
| `showScrollBar` | No | Whether to show or not the scroll bar / scroll indicator | `true` |
| `numColumns` | No | How many columns of gifs to show. When this is used, `horizontal` is automatically set to false | |
| `onGifLongPress` | No | Function to be called when the user long presses on a gif. The parameter of this function is a string with the url of the gif in better quality | |


# License
[ISC](LICENSE)
