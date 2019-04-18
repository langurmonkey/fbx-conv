# fbx-conv

This is my fork of `fbx-conv` using 32-bit integer indices instead of 16-bit shorts for use in [Gaia Sky](https:/gitlab.com/langurmonkey/gaiasky).

Command line utility using the FBX SDK to convert [FBX/Collada/Obj files](http://docs.autodesk.com/FBX/2014/ENU/FBX-SDK-Documentation/files/GUID-0B122E01-7DB8-48E3-AADA-5E85A197FEE1.htm)
to more runtime friendly formats. The FBX content is parsed into an
in-memory datastructure. Pluggable writers then take this datastructure
to generate the output. Send us a pull request if you want the writer
for your engine/framework/app to be integrated.

## Command-line Usage

``` bash
$  fbx-conv [options] <input> [<output>]
```

### Options/flags

*   **`-?`**				-Display help information.
*   **`-o <type>`**			-Set the type of the output file to <type>
*   **`-f`**				-Flip the V texture coordinates.
*   **`-p`**				-Pack vertex colors to one float.
*   **`-m <size>`**			-The maximum amount of vertices or indices a mesh may contain (default: 32k)
*   **`-b <size>`**			-The maximum amount of bones a nodepart can contain (default: 12)
*   **`-w <size>`**			-The maximum amount of bone weights per vertex (default: 4)
*   **`-v`**				-Verbose: print additional progress information

#### Example

``` bash
$  fbx-conv -o g3db myModel.obj convertedModel.g3db
```

## Building and installing

This verison only supports Linux.

Download [FBX SDK 2014](https://www.autodesk.com/developer-network/platform-technologies/fbx-sdk-2014-2-1) and install it somewhere (`/path/to/fbx-sdk-2014`). Then, set the `FBX_SDK_ROOT` to the directory where you installed the FBX SDK, and finally make and install. Here is the full sequence:

``` bash
$  export FBX_SDK_ROOT=/path/to/fbx-sdk-2014
$  make && sudo make install
```

