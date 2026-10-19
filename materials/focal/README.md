# Focal gallery photographic PBR materials

Powered by [Poly Haven](https://polyhaven.com). All 12 texture assets are [CC0](https://polyhaven.com/license). These are photographic library materials used for a reconstruction; they are **not measured scans of the museum**.

| Prefix | Official source | One UV tile | Authors |
| --- | --- | --- | --- |
| plaster | [Beige Wall 001](https://polyhaven.com/a/beige_wall_001) | 3 × 3 m | Dimitrios Savva (Photography); Rico Cilliers (Processing) |
| timber | [Wood Table 001](https://polyhaven.com/a/wood_table_001) | 1.5 × 1.5 m | Dimitrios Savva (Photography); Rico Cilliers (Processing) |
| stone | [Granite Tile](https://polyhaven.com/a/granite_tile) | 2.3 × 2.3 m | Charlotte Baglioni (All) |
| fabric | [Terlenka](https://polyhaven.com/a/terlenka) | 0.265708 × 0.2663 m | colormass (Photography); Rico Cilliers (Processing) |

Each material has a 1024 × 1024 color, OpenGL normal, and roughness WebP plus one provenance JSON per image. The manifest records output byte counts, SHA-256 hashes, physical dimensions, source URLs, authors, and color-space intent.

Color maps retain source color: resize and quality-95 WebP conversion only. Normal and roughness use lossless WebP. Normals are tangent-space OpenGL (+Y), with no green-channel inversion. Color uses sRGB; normal and roughness must remain linear/non-color data. Roughness is the source Rough map, not an inverted gloss map.

For full physical scale use repeat = surface width / tile width, surface height / tile height. For wood joinery align the original grain to the long member axis using geometry UVs. The floor's brown tone should be an explicit material tint, not a modification of the source albedo. Keep source roughness variation active. Do not enlarge the fabric tile to room scale.

Rebuild from the project root with `node scripts/fetch-focal-materials.mjs`. The default is cache-first, so completed sources are reused without network calls. For a guaranteed offline rebuild use `node scripts/fetch-focal-materials.mjs --offline`. Sources and API snapshots are under `research/focal-material-sources/`; downloaded source hashes are checked against official API MD5 and size before conversion. To refresh a particular source deliberately remove only its local cached file, then rerun online.

The download script identifies itself with a non-default User-Agent, makes a finite number of build-time requests, and does not contact Poly Haven from the running app.
