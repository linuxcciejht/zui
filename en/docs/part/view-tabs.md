# Tabs

<div class="alert alert-warning">
  <h4>Compatibility</h4>
  <ul>
    <li>There may be compatibility issues in the browser of your mobile device.</li>
  </ul>
</div>

## Examples

<div class="example">
  <div class="tabs" id="tabsExample"></div>
</div>

```html
<div class="tabs" id="tabsExample"></div>
```

```js
// Definition tab
var tabs = [{
    title: 'iframe example',
    url: 'docs/partial/iframe-tab.html',
    type: 'iframe',
    forbidClose: true
}, {
    title: 'Ajax example',
    url: 'docs/partial/remote-tab.html',
    type: 'ajax'
}, {
    title: 'Custom example',
    icon: 'icon-star',
    type: 'custom',
    content: function() {
        return '<div class="alert alert-block alert-success"><p>The content here is dynamically generated by functions. Update when the following time is refreshed.</p><p>' + (new Date().format('yyyy-MM-dd hh:mm:ss')) +   '</p></div>';
    }
}, {
    title: 'MZUI',
    url: 'http://openzui.com/m',
    type: 'iframe'
}, {
    defaultTitle: 'Unable to load the tab.',
    url: 'http://zui1.sexy'
}];

// Initialize tabs
$('#tabsExample').tabs({tabs: tabs});
```

## Options

<table class="table table-bordered">
  <thead>
    <tr>
      <th style="width: 140px">Option</th>
      <th style="width: 150px">Name</th>
      <th style="width: 150px">Value</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>tabs</code></td>
      <td>Initial tab list</td>
      <td>Default: `[]`</td>
      <td>Specify an array of tab objects to define the tabs that are displayed after the tabs is initialized. Tab page object definitions are as follows.</td>
    </tr>
    <tr>
      <td><code>defaultTab</code></td>
      <td>Default activated tab ID</td>
      <td>Default: `null`</td>
      <td>If set as null(`null`), the first tab in the initial tab list will be activated after the tab is initialized.</td>
    </tr>
    <tr>
      <td><code>contextMenu</code></td>
      <td>Whether to enable the context menu</td>
      <td>Default:`true`</td>
      <td>If set as `true`, enable context menus on the navigation to facilitate user actions on tabs. When using a mouse, right click to display a menu.</td>
    </tr>
    <tr>
      <td><code>defaultTabIcon</code></td>
      <td>Default tab icon</td>
      <td>Default: `'icon-window'`</td>
      <td>Use icon class name in [Control->icon]('#control/icon') to set the tab page. Use this option as the default icon if there is no tab icon property specified in the tab object.</td>
    </tr>
    <tr>
      <td><code>showMessage</code></td>
      <td>Whether to display an error message</td>
      <td>Default: `true`</td>
      <td></td>
    </tr>
    <tr>
      <td><code>errorTemplate</code></td>
      <td>Error message template string</td>
      <td>Default: `'<div class="alert alert-block alert-danger with-icon"><i class="icon-warning-sign"></i><div class="content">{0}</div></div>'`</td>
      <td></td>
    </tr>
    <tr>
      <td><code>messagerOptions</code></td>
      <td>Popout message option</td>
      <td>`null`</td>
      <td>When a popout message is displayed, use this option to set an object for [Messager](javascript/messager) parameter.</td>
    </tr>
    <tr>
      <td><code>lang</code></td>
      <td>Current interface language</td>
      <td>Default: `'zh_cn'`</td>
      <td>
        <p>So the available options are:</p>
        <ul>
          <li>`zh_cn`: Use simplified Chinese interface;</li>
          <li>`zh_tw`: Use traditional Chinese interface;</li>
          <li>`en`: Use English interface;</li>
          <li>
            <p>Or specify an object to customize the language text, e.g.:</p>
            <pre><code>{
    reload: 'Reload',
    close: 'Close',
    closeOthers: 'Close other tabs',
    closeRight: 'Close the right tab',
    reopenLast: 'Restore last closed tab',
    errorCannotFetchFromRemote: 'Unable to get contents from remote server ({0}).'
}</code></pre>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Tab page objects

Each tab uses an object to store related information. Define the default label in the tabs by defining an array of tab objects to be passed to the initialization function at the initialization. You also need to define a tab object when you need to dynamically open a tab. Attributes supported by tab objects include:

<table class="table table-bordered">
  <thead>
    <tr>
      <th style="width: 140px">Option</th>
      <th style="width: 150px">Name</th>
      <th style="width: 150px">Value</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>id</code></td>
      <td>Unique identifier of the tab</td>
      <td>Automatically generated by default</td>
      <td>Generally it does not need to be specified. If you need to manage the label object, you need to set a globally unique string for getting the tab object next time.</td>
    </tr>
    <tr>
      <td><code>type</code></td>
      <td>Tab content type</td>
      <td>Default:`'auto'`</td>
      <td>
        <p>All available values include:</p>
        <ul>
          <li>`'iframe'`: use iframe to load a remote page;</li>
          <li>`'ajax'`: use ajax to load remote content;</li>
          <li>`'custom'`: use `content` value as the content. If `content` is a function, the function returns the value as the content;</li>
          <li>`'auto'`: Automatically set based on other attributes. If set `url` attribute and `ajax` attribute is set as `ajax`, it is `iframe`. If not, set `url` attribute as `custom`.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>url</code></td>
      <td>Remote content address</td>
      <td>Default: `''`</td>
      <td>If `type` attribute is `iframe`, it is the remote page address. If `type` is `ajax`, it is used as the remote content request address.</td>
    </tr>
    <tr>
      <td><code>ajax</code></td>
      <td>ajax Request parameter</td>
      <td>Default: `{type: 'GET'}`</td>
      <td>An object can be used to define jQuery Ajax Request parameter.</td>
    </tr>
    <tr>
      <td><code>icon</code></td>
      <td>Tab icon</td>
      <td>Default: `'icon-window'`</td>
      <td>Use icon class names in [Control->icon]('#control/icon') to set the tab page. The default is `'icon-window'` which can be set in `defaultTabIcon`.</td>
    </tr>
    <tr>
      <td><code>title</code></td>
      <td>Tab title</td>
      <td>Default: `''`</td>
      <td>When the tab title is set as empty `''` and tab type(`type`) is `'iframe'`, get iframe page title as the tab title.</td>
    </tr>
    <tr>
      <td><code>defaultTitle</code></td>
      <td>Tab page default title</td>
      <td>Default: `''`</td>
      <td>When the tab title is set as empty `''` and tab type(`type`) is `'iframe'`, get iframe page title as the tab title. Default title is used if the tab is not loaded.</td>
    </tr>
    <tr>
      <td><code>forbidClose</code></td>
      <td>Whether to prohibit tabs from being manually closed</td>
      <td>Default: `false`</td>
      <td>If set as `true`, user is not allowed to close this tab.</td>
    </tr>
    <tr>
      <td><code>onCreate</code></td>
      <td>Callback function when the tab is created</td>
      <td>Default: `null`</td>
      <td>This callback function contains a parameter for the tab page object.</td>
    </tr>
    <tr>
      <td><code>onOpen</code></td>
      <td>Callback function when the tab opens</td>
      <td>Default: `null`</td>
      <td>This callback function contains a parameter for the tab page object.</td>
    </tr>
    <tr>
      <td><code>onClose</code></td>
      <td>Callback function when the tab is closed</td>
      <td>Default: `null`</td>
      <td>This callback function contains a parameter for the tab page object.</td>
    </tr>
    <tr>
      <td><code>createTime</code>(Read only)</td>
      <td>Timestamp created by the tab page object</td>
      <td>Default: `0`</td>
      <td>This tab can be used to get the timestamp created by the tab object when the tab is created in the tabs.</td>
    </tr>
    <tr>
      <td><code>openTime</code>(Read only)</td>
      <td>The timestamp when the tab was last opened</td>
      <td>Default: `0`</td>
      <td>This tab can be used to get the timestamp of the last time the tab was opened when the tab was created in the tabs.</td>
    </tr>
    <tr>
      <td><code>loaded</code>(Read only)</td>
      <td>The timestamp of the last content loading of the tab page</td>
      <td>Default: `0`</td>
      <td>When the tab is created, this property can be used to get the timestamp of the content loaded by the tab last time.</td>
    </tr>
  </tbody>
</table>

## Methods

### `open(tab)`

Open and activate a tab. If this tab is opened for the first time, load the tab content. The parameters are defined as follows:

* `tab`: Tab page object, or automatically create a tab object using a remote server address string as a parameter;
* `forceReload`: Optional parameter. If set as `true`, force the tab to reload the content even if the tab content has been loaded. Equivalent to reloading(Refresh).

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Tab object to be opened
var myTab = {
    url: 'http://openzui.com',
    type: 'iframe',
    defaultTitle: 'ZUI Official website'
};
// Open the tab
myTabs.open(myTab);
```

```js
// When the tab type is iframe, iframe address can also be used as a parameter.
myTabs.open('http://openzui.com');
```

### `close(tabId, forceClose)`

Close the tab. Its parameters are defined as:

* `tabId`: Id of the tab object to be closed;
* `forceClose`: Optional. If set as `true`, force to close the tab even when `forbidClose` is set as `true`.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Close the tab
myTabs.close('myCloseTabId');
```

### `getTab(tabId)`

According to the tab page ID to get the tab object. Its parameters are defined as follows:

* `tabId`: ID of the tag object to get.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Get the currently active tab object
var mySpecialTab = myTabs.getTab('mySpecialTabId');
console.log('The title of the page obtained is', mySpecialTab.title);
```

### `getActiveTab()`

Get the currently active tab object.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Get the currently active tab object
var myActiveTab = myTabs.getActiveTab();
console.log('The currently active tab title is', myActiveTab.title);
```

### `reload(tab)`

Reload tab content. Its parameters are defined as follows:

* `tab`: The tab object to be reloaded. Reload the currently active tab if this parameter is not specified.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Reload the currently active tab
myTabs.reload();

// Get the tab object to load
var myTab = myTabs.getTab('reloadTabId');

// Reload the tab
myTabs.reload(myTab);
```

### `closeOthers(tabId)`

Close tabs other than the current tab. Its parameters are defined as follows:

`tabId`：Current tab ID.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Close tabs other than the current tab
myTabs.closeOthers('tabID');
```

### `closeRight(tabId)`

CLose the tabs to the right of the current tab on the navigation. Its parameters are defined as follows:

`tabId`: Current tab ID.

```js
// Get the tab object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Close the tabs to the right of the current tab on the navigation
myTabs.closeRight('tabID');
```

### `closeAll()`

Close navigation to all tabs.

```js
// Get the tab manager object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Close all tabs
myTabs.closeAll();
```

### `reopen()`

Reopen the last closed tab.

```js
// Get the tab manager object instance
var myTabs = $('#myTabs').data('zui.tabs');

// Reopen the last closed tab
myTabs.reopen();
```

## Events

### `onOpen`

Triggered when the tab is open. Event callback function `this` is the instance of the current tab manager instance. The parameters are defined as follows:

* `tab`: Currently open tab object.

```js
// Set the event callback function at the initialization
$('#myTabs').tabs({
    onOpen: function(tab) {
        console.log('Bookmark page ' + tab.title + ' is open.');
    }
});
```

```js
// Use jQuery $().on() listen events
$('#myTabs').on('onOpen', function(event, tab) {
    console.log('Bookmark page ' + tab.title + ' is open.');
});
```

### `onLoad`

Triggered when the tab is loaded. Event callback function `this` is the instance of the current tab manager. The parameters are defined as follows:

* `tab`: Currently loaded tab object.

```js
// Set the event callback function at the initialization
$('#myTabs').tabs({
    onLoad: function(tab) {
        console.log('Bookmark page ' + tab.title + ' loading is complete.');
    }
});
```

```js
// Use jQuery $().on() listen events
$('#myTabs').on('onLoad', function(event, tab) {
    console.log('Bookmark page ' + tab.title + ' loading is complete.');
});
```

### `onClose`

Triggered when the tab is closed. Event callback function `this` is the instance of the current tab manager. The parameters are defined as follows:

* `tab`: Tab object that is closed.

```js
// Set the event callback function at the initialization
$('#myTabs').tabs({
    onClose: function(tab) {
        console.log('Bookmark page ' + tab.title + ' is closed.');
    }
});
```

```js
// Use jQuery $().on() listen events
$('#myTabs').on('onClose', function(event, tab) {
    console.log('Bookmark page ' + tab.title + ' is closed.');
});
```

## Customize

Use `.tabs-navbar` element and `.tabs-container` element in tab initialization elements to define the navigation and tab content in the parent element.

``` html
<div id="myTabs" class="tabs">
  <nav class="tabs-navbar"></nav>
  <nav class="tabs-container"></nav>
</div>
```

<script src="../dist/lib/tabs/zui.tabs.js"></script>
<link href="../dist/lib/tabs/zui.tabs.css" rel="stylesheet">
<script>
function afterPageLoad() {
    $('#tabsExample').tabs({
        tabs: [{
            title: 'iframe example',
            url: 'docs/partial/iframe-tab.html',
            type: 'iframe',
            forbidClose: true
        }, {
            title: 'Ajax example',
            url: 'docs/partial/remote-tab.html',
            type: 'ajax'
        }, {
            title: 'Custom example',
            icon: 'icon-star',
            type: 'custom',
            content: function() {
                return '<div class="alert alert-block alert-success"><p>The content here is dynamically generated by functions. Update when the following time is refreshed.</p><p>' + (new Date().format('yyyy-MM-dd hh:mm:ss')) +   '</p></div>';
            }
        }, {
            title: 'MZUI',
            url: 'http://openzui.com/m',
            type: 'iframe'
        }, {
            defaultTitle: 'Unable to load tab',
            url: 'http://zui1.sexy'
        }]
    });
}
</script>