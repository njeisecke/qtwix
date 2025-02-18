# Qt WiX

Contains WiX components for the [Qt](http://www.qt.io) runtime.

Should be used as a `git submodule`.

## Usage

### Branches

Use the branch or tag that corresponds to the target Qt version. The structure
of Qml plugins and the version of the ffmpeg libraries tend to change from time
to time.

### Wix

Add `ComponentGroupRef` entries for the required modules:

    <Feature Id="ProductFeature" Title="My Application" Level="1">
      <ComponentGroupRef Id="CMP_MyApp" />
      <!-- Qt -->
      <ComponentGroupRef Id="CMP_QtCore" />
      <ComponentGroupRef Id="CMP_QtGui" />
      <ComponentGroupRef Id="CMP_QtWidgets" />
      <ComponentGroupRef Id="CMP_QtPrintSupport" />
      <ComponentGroupRef Id="CMP_QtQuick" />
      <ComponentGroupRef Id="CMP_QtQuickDialogs" />
      <ComponentGroupRef Id="CMP_QtQuickWidget" />
      <ComponentGroupRef Id="CMP_QtQuickLabsPlatform" />
      <ComponentGroupRef Id="CMP_QtNetwork" />
      <ComponentGroupRef Id="CMP_QtNetworkAuth" />
      <ComponentGroupRef Id="CMP_QtSql" />
      <ComponentGroupRef Id="CMP_QtWebSockets" />
      <ComponentGroupRef Id="CMP_QtWebEngine" />
      <ComponentGroupRef Id="CMP_QtWebEngineQuick" />
      <ComponentGroupRef Id="CMP_QtWebChannel" />
      <ComponentGroupRef Id="CMP_QtWebChannelQuick" />
      <ComponentGroupRef Id="CMP_QtPositioning" />
      <ComponentGroupRef Id="CMP_QtMultimedia" />
      <ComponentGroupRef Id="CMP_QtMultimediaQuick" />
      <ComponentGroupRef Id="CMP_QtTranslation_de" />
      <ComponentGroupRef Id="CMP_QtTranslation_it" />
    </Feature>

Apply `candle` on each required module to compile a `.wixobj`.

Add those object files to the `light` linker invocation.

## Translations

For now, only german and italian translation are available as components. Feel
free to add other languages.

## Dependencies

* `QtWebEngine` depends on `QtPositioning` and `QtWebChannel`
* `QtWebEngineQuick` depends on `QtWebChannelQuick`

Make sure to include the components, otherwise the application won't start.
