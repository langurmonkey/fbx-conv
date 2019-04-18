# fbx-conv

This is my fork of `fbx-conv` using 32-bit integer indices instead of 16-bit shorts for use in [Gaia Sky](https:/gitlab.com/langurmonkey/gaiasky).

Command line utility using the FBX SDK to convert [FBX/Collada/Obj files](http://docs.autodesk.com/FBX/2014/ENU/FBX-SDK-Documentation/files/GUID-0B122E01-7DB8-48E3-AADA-5E85A197FEE1.htm)
to more runtime friendly formats. The FBX content is parsed into an
in-memory datastructure. Pluggable writers then take this datastructure
to generate the output. Send us a pull request if you want the writer
for your engine/framework/app to be integrated. We'll build the
converter for Windows, Linux and Mac.

The FBX parser is largely based on GamePlay SDK's encoder. We'll try to 
back-port any bug fixes or improvements.

## Command-line Usage

*   Windows - `fbx-conv-win32.exe [options] <input> [<output>]`
*   Linux - `fbx-conv-lin64 [options] <input> [<output>]`
*   Mac - `fbx-conv-mac [options] <input> [<output>]`

### Options/flags
*   **`-?`**				-Display help information.
*   **`-o <type>`**			-Set the type of the output file to <type>
*   **`-f`**				-Flip the V texture coordinates.
*   **`-p`**				-Pack vertex colors to one float.
*   **`-m <size>`**			-The maximum amount of vertices or indices a mesh may contain (default: 32k)
*   **`-b <size>`**			-The maximum amount of bones a nodepart can contain (default: 12)
*   **`-w <size>`**			-The maximum amount of bone weights per vertex (default: 4)
*   **`-v`**				-Verbose: print additional progress information

### Example
`fbx-conv-win32.exe -f -v myModel.fbx convertedModel.g3db`

##Building

You'll need premake and an installation of the FBX SDK 2014. Once installed/downloaded, set the
FBX_SDK_ROOT to the directory where you installed the FBX SDK. Then run one of the 
generate_XXX scripts. These will generate a Visual Studio/XCode project, or a Makefile.
