Spatial Grid Referencing Protocol (SGR)
AIon Technology — Multimodal Interaction Standard, Phase 1
1. Introduction
The Spatial Grid Referencing Protocol (SGR) is the foundational layer of AIon Technology’s multimodal interaction standard.
It establishes a universal spatial language that allows humans and AI systems to communicate precise, deterministic editing intent inside any image.

SGR is model‑agnostic, provider‑agnostic, and future‑proof.
It does not replace AI models — it gives them structure.

This protocol is Phase 1 of AIon Technology’s multimodal standard.
Phase 2 extends the same principles to audio.
Phase 3 extends them to video.

2. Purpose of the Protocol
SGR solves the core limitation of modern AI image systems:

AI models cannot reliably edit specific regions of an image.

They regenerate entire images, misinterpret instructions, and produce inconsistent results.

SGR introduces:

deterministic regional control

explicit spatial intent

predictable editing behavior

minimal compute waste

universal compatibility

This transforms image editing from guesswork into engineering.

3. Core Concepts
3.1 Universal Grid
SGR overlays a grid on any image, regardless of:

resolution

aspect ratio

provider

model architecture

The default grid is 12×12, but the protocol supports any N×N configuration.

Each cell is referenced as:

Código
(row, column)
Example:

Código
(3, 5) = row 3, column 5
3.2 Regions
A region is a set of grid cells.

Example:

Código
region: [(3,4), (3,5), (4,4), (4,5)]
Regions can be:

rectangular

irregular

single‑cell

multi‑cell

3.3 Intent
The user specifies the desired modification.

Examples:

“change the color to red”

“remove the object”

“add a reflection”

“make it brighter”

3.4 Constraints
Optional rules that guide the model.

Examples:

“preserve lighting”

“do not alter background”

“keep proportions”

3.5 Output Expectation
Defines what the model should return.

Examples:

“only modify the region”

“preserve global style”

“maintain original resolution”

4. Protocol Structure
SGR instructions are transmitted as a structured payload.

4.1 Payload Format (JSON)
json
{
  "protocol": "SGR-1.0",
  "grid_size": 12,
  "region": [[3,4], [3,5], [4,4], [4,5]],
  "intent": "change the color to red",
  "constraints": ["preserve lighting", "maintain texture"],
  "output": "modify only the selected region"
}
4.2 Provider-Agnostic Execution
SGR does not dictate how the model performs the edit.
It only defines what must be edited and where.

Any provider can implement SGR:

OpenAI

Google

xAI

Midjourney

Runway

Adobe

Meta

Kling

Luma

5. Interaction Flow
Step 1 — User selects region
UI or API defines the grid cells.

Step 2 — User defines intent
Natural language or structured command.

Step 3 — SGR builds the payload
The protocol converts the instruction into a deterministic structure.

Step 4 — Provider receives the payload
The model interprets the instruction with explicit spatial context.

Step 5 — Provider returns modified image
Only the specified region is altered.

6. Error Handling
SGR defines standard error types:

SGR-ERR-01: Invalid grid size

SGR-ERR-02: Region out of bounds

SGR-ERR-03: Empty region

SGR-ERR-04: Unsupported provider

SGR-ERR-05: Missing intent

Errors must be returned in structured form:

json
{
  "error": "SGR-ERR-02",
  "message": "Region contains coordinates outside the grid."
}
7. Audio Extension (Phase 2)
The audio protocol extends the same philosophy:

precise segmentation

deterministic control

region‑based editing (temporal instead of spatial)

Audio uses temporal grids instead of spatial grids.

Example:

Código
grid_size: 48 (48 segments per minute)
region: [12–18]
intent: "remove background noise"
This keeps the multimodal standard unified.

8. Video Extension (Phase 3)
Video combines:

spatial grid (SGR)

temporal grid (audio protocol)

This creates a 3D grid:

Código
(x, y, t)
Allowing frame‑accurate, region‑accurate editing.

9. Security & Validation
SGR includes optional validation layers:

region boundary checks

intent classification

provider compatibility checks

payload integrity hashing

These ensure safe and predictable execution.

10. Versioning
SGR uses semantic versioning:

1.x — image protocol

2.x — audio extension

3.x — video extension

11. Licensing
SGR is proprietary technology licensed by AIon Technology.

See the README for full licensing details.

12. Contact
For licensing, partnerships, or evaluation access:

AIon Technology  
DM via X: https://x.com/JesusRo46738821
Email: jesus05rocio22@hotmail.com
