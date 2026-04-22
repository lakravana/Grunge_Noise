<div align="center"><h1>Grunge Noise / Photocopy DCTL</h1><p><strong>Version 1.0 | Analog Photocopy & CRT Texture Simulation</strong></p><p>Created by Galavnikov @ lakravana.com</p></div><hr><h3>1. Logline</h3>
<p>
A high-contrast "stamping" engine that converts images into stylized black-and-white art by injecting procedural noise (White, Pink, or Perlin) into the luminance signal before applying a binary threshold.
</p><hr><h3>2. The Creative Gap</h3>
<p>
Standard digital thresholding is mathematically "perfect," resulting in clean, clinical edges that look like vector art rather than physical media. This "perfection" lacks the organic grit, ink bleed, and paper grain found in vintage xerography, faxes, or low-resolution CRT displays.
</p>
<p>
Before this script, creating a "grunge" or "dirty" photocopy look required complex stacking of external textures and luma keys. There was no single tool capable of generating procedural grain that actually <em>interacts</em> with the image highlights and shadows to "break" the edges of the high-contrast transition.
</p><hr><h3>3. The Solution & Mathematical Logic</h3><p>The Grunge Noise DCTL solves this by treating the image as a physical substrate where noise and luminance are blended before the final "ink" is applied.</p><ul>
<li><strong>Procedural Grain Generation:</strong> The script generates three distinct mathematical noise types:
<ul>
<li><strong>White Noise:</strong> Pure random high-frequency distribution for a digital "glitch" look.</li>
<li><strong>Pink Noise:</strong> A fractal Brownian motion (FBM) approximation that clusters pixels for a more organic, "sandy" texture.</li>
<li><strong>Perlin Noise:</strong> Uses cubic interpolation (Hermite) to create smooth, cloudy "blobs" that simulate ink pooling or paper mold.</li>
</ul>
</li>
<li><strong>Luma-Noise Overlay:</strong> Instead of adding noise on top of the image, the script uses an <strong>Overlay Blend Mode</strong>. This mathematically pushes the noise into the midtones while protecting the absolute blacks and whites, ensuring the texture feels embedded in the image's lighting.</li>
<li><strong>Local Masking (Ink Bleed):</strong> The "Local Mask" parameter applies a spatial box blur to the combined luma/noise map. This simulates the way light scatters or ink bleeds into paper fibers before the final high-contrast thresholding occurs.</li>
<li><strong>Binary Threshold Gating:</strong> Finally, the processed signal is compared against a user-defined threshold. Any pixel above the value becomes pure white ($1.0$), and everything else becomes pure black ($0.0$), resulting in the iconic "Xerox" stamp.</li>
</ul><hr><h3>4. GUI / Interface Elements</h3><table>
<thead>
<tr>
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Enable B&W</strong></td>
<td>Master toggle to activate the high-contrast photocopy effect.</td>
</tr>
<tr>
<td><strong>B&W Threshold</strong></td>
<td>Determines the "ink level." Higher values result in more black (less exposure), while lower values create a thinner, "washed-out" photocopy.</td>
</tr>
<tr>
<td><strong>Enable Grey Filter</strong></td>
<td>Activates the procedural noise injection layer.</td>
</tr>
<tr>
<td><strong>Filter Grain Type</strong></td>
<td>Selects between <strong>White</strong> (sharp), <strong>Pink</strong> (textured), or <strong>Perlin</strong> (organic/cloudy) noise structures.</td>
</tr>
<tr>
<td><strong>Filter Saturation / Texture</strong></td>
<td>Controls how much the noise "distorts" the luminance map before thresholding.</td>
</tr>
<tr>
<td><strong>Filter Grain</strong></td>
<td>Sets the physical size of the noise "pixels." Higher values simulate a low-resolution scan or coarse paper grain.</td>
</tr>
<tr>
<td><strong>Local Mask</strong></td>
<td>Adds spatial smoothing. Increasing this creates "softer" ink edges and mimics the light-bleed of a physical photocopy glass.</td>
</tr>
</tbody>
</table><hr>
