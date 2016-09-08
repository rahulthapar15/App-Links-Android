##Indexing For Android Developers (PART 1)
######App Links is an open standard to deep link to content in your app. When someone uses your app to share content on Facebook or any other App Links enabled app, you can make a link that makes it possible to jump back into your app from that piece of content.

``Implementation``

`FLOW : `
<li>Create a new App Link object. You can set up an object for one platform or several at the same time.</li></li>
<li>Save the App Link object ID that's returned.
<li>Use that ID to get the URL you can use to share the content.</li>
<li>Configure additional platforms that you support.</li>
<li>Configure your app's manifest file for the configured URLs.</li>


* * *
``You create a new App Link object for a content targeted to Android like this:``

```PHP
-F access_token="APP_ACCESS_TOKEN" \
-F name="Android App Link " \
-F android=' [
    {
      "url" : "sharesample://story/1234",
      "package" : "com.applink.rahulthapar.sample1.sharesample",
      "app_name" : "ShareSample",
    },
  ]' \
-F web=' {
    "should_fallback" : false,
  }'
```
``A successful call returns an ID that represents the App Link object``
```PHP
{"id":"123456789734299"}

```
``*YOUR_APP_LINK_HOST_ID* ==represents the id returned from creating your App Link object. Your response will look like this:``

```PHP
{
   "canonical_url": "https://fb.me/643402985734299",
   "id": "123456789734299"
}
```
* * *
``In ANDROID Manifest File :``
```HTML
<activity android:name=".MainActivity"
    android:label="@string/app_name" >
    ...
    <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data android:scheme="sharesample" />
    </intent-filter>
</activity>
```
