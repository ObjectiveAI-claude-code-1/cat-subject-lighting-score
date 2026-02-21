# cat-subject-lighting-score

Scores how well lighting in a cat photograph reveals the subject. Evaluates facial legibility (eyes, whiskers, expression), fur and color fidelity (texture, true colors, patterns), and body form wholeness (posture, subject-background separation). Rewards clarity over artistry — plain light that shows the cat outscores drama that obscures it.

## Input

The function accepts a single input:

| Field | Type | Required | Description |
|---|---|---|---|
| `cat_photo` | image | Yes | A photograph containing a cat as its subject. |

The photograph can come from any source — a professional portrait, a phone snapshot, a shelter intake photo, or a breeder listing image. The function evaluates the image as-is, without regard for the photographer's intent, equipment used, or artistic goals. It looks only at the result.

## Output

A scalar score between **0** and **1**.

- **1.0** — The lighting fully reveals the cat. The face is legible, the coat is faithfully rendered, and the body reads as a whole, coherent subject.
- **0.5** — The lighting partially serves the cat. Some features are visible but others are compromised by shadow, overexposure, contrast, or color distortion.
- **0.0** — The lighting fails the cat. The subject is obscured — lost in darkness, washed into featureless brightness, fragmented by extreme contrast, or distorted beyond recognition.

The final score is the weighted average of three independent evaluation tasks, each targeting a different dimension of how light reveals the cat.

## What It Evaluates

### 1. Facial Legibility

The face is the anchor of the subject — the first place a viewer's eye goes. This task evaluates whether the lighting allows a viewer to clearly see the cat's eyes, nose, whiskers, ears, and expression.

**Scores well when:**
- Both eyes are visible and defined
- The nose, whiskers, and ears are discernible
- The expression is readable (alert, relaxed, curious, sleepy)
- The face is evenly and naturally illuminated

**Scores poorly when:**
- The face is overexposed into a flat, featureless white shape
- Half the face is cast into impenetrable shadow
- Extreme contrast fractures the features into disconnected bright spots and dark voids

### 2. Fur and Color Fidelity

A cat's coat — its color, pattern, and texture — is one of its most defining visual characteristics. This task evaluates whether the lighting reveals the coat truthfully and tangibly.

**Scores well when:**
- Fur texture is visible (short and sleek, long and flowing, dense and plush)
- Colors appear natural and accurate without unnatural casts
- Patterns such as stripes, spots, or points are distinct and readable

**Scores poorly when:**
- The coat is washed out into a featureless bright mass
- Fur texture is lost in shadow or overexposure
- The light source imposes a strong unnatural color cast (green from fluorescents, orange from tungsten, harsh blue-white from bare LEDs)
- Patterns are flattened or swallowed by extreme lighting

### 3. Body Form and Wholeness

A cat is a physical animal with a posture, shape, and presence within the frame. This task evaluates whether the lighting allows the viewer to perceive the cat as a complete, coherent subject.

**Scores well when:**
- The cat's body is clearly distinguishable from the background
- The full posture and physical form are visible (size, proportions, limb arrangement)
- The cat reads as a distinct, whole creature within the frame

**Scores poorly when:**
- Extreme contrast splits the body into disconnected islands of visibility
- The cat merges into a dark background due to insufficient lighting
- Overexposure erases the boundaries of the cat's form against a bright background
- The viewer perceives fragments rather than a complete animal

## Use-Cases

- **Animal shelters and rescue organizations** — Identify which adoption listing photos clearly show the cat and which need to be retaken. Clear photographs directly influence adoption rates.
- **Veterinary telemedicine** — Assess whether a pet owner's photo is clinically useful for remote consultations. Fur quality, body shape, and visible features are diagnostic inputs that require adequate lighting.
- **Breeders, registries, and marketplaces** — Ensure listing photographs accurately show breed-specific features, coat patterns, and physical conformation to buyers and judges.
- **Photo quality filtering** — Automatically flag or rank cat photographs by subject visibility in any application where clear depiction of the animal matters.

## Philosophy

This function is indifferent to photographic style and devoted to clarity. It does not reward dramatic lighting for its own sake, nor does it penalize simplicity. A kitchen ceiling light that plainly illuminates a cat will outscore golden-hour backlighting that turns the cat into a silhouette. The sole question is functional: **can a viewer look at this photograph and understand what the cat looks like?**