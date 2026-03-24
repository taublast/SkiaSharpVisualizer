# SkiaSharpVisualizer
A Visual Studio debugger extension for viewing [SkiaSharp](https://github.com/mono/SkiaSharp) bitmaps, images and surfaces.

## Building
Designed for Visual Studio 2026 and recent Visual Studio 2022 builds from 17.14 onward. Install the "Visual Studio extension development" workload. 
After building the solution, run the generated .vsix file to install.

## Architecture
The solution consists of two projects:

- `SkiaSharpVisualizer` is the VisualStudio.Extensibility VSIX host that runs the out-of-process extension UI and debugger visualizer provider.
- `SkiaSharpVisualizerSource` is the `VisualizerObjectSource` payload assembly that Visual Studio uses to serialize SkiaSharp objects from the debuggee side.

That split is required by the debugger visualizer architecture. Merging them into one project would couple the object-source payload to the VSIX host runtime and make packaging and loading more fragile.

## How to Use
The extension adds a new UI item to view SkiaSharp SKBitmap, SKImage, and SKSurface objects.
![image](https://github.com/MapLarge/SkiaSharpVisualizer/assets/38544371/932c0544-dea0-445a-a052-e971878af182)

When viewing, you will see a tool window containing a graphical preview of the image.
![image](https://github.com/MapLarge/SkiaSharpVisualizer/assets/38544371/5d4fafcd-79e1-4b07-86ed-f92d362c3a4f)

The stretch option will make the image fill the entire dialog space.
![image](https://github.com/MapLarge/SkiaSharpVisualizer/assets/38544371/53b09954-003d-45f6-a494-1ad2cd72771a)

The bordered option will add an indicator border around the image so you can figure out the boundary of an image with transparency.
![image](https://github.com/MapLarge/SkiaSharpVisualizer/assets/38544371/771741e4-413d-4414-97d9-c59cdfddf2a7)

The "Open in External Viewer" button will launch the default viewer for PNG files.
![image](https://github.com/MapLarge/SkiaSharpVisualizer/assets/38544371/327bf856-cace-4d09-9c7c-7c5d5b31c5b3)

## Notes
Accessing GPU memory from debugger could crash Visual Studio so GPU-backed instances are reported as unsupported by the viewer.

## Contributing
PRs and suggestions are welcome, or you can fork this project and make your own enhancements.
