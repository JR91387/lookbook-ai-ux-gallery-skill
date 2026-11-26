# Lookbook style catalog

Reference previews: chrislemke/website_designs (MIT), `https://chrislemke.github.io/website_designs/examples/<Name>.html`, guide at `designs/<Name>.md`. The "Ref" column gives `<Name>`; ≈ means closest match, not the same style.
Google example: ✓ = well-known example; ? = check before quoting it as fact.

| Style | Definition | Feel | Google example | Ref |
|---|---|---|---|---|
| Claymorphism | Puffy, rounded 3D shapes with soft inner and outer shadows, like molded clay | Friendly, toylike, tactile | ? Duolingo (cited by superdesign.dev); "Dribbble claymorphism" | Claymorphism |
| Cybercore | Late-90s/early-2000s internet: binary, wireframe globes, chrome, neon on black, tech-optimism | Nostalgic, techy, buzzing | ? "Aesthetics Wiki Cybercore" | ≈ Early_Cyber |
| Neo-Brutalism | Thick black borders, hard offset shadows, flat loud colors, raw type | Blunt, playful, confident | ✓ Gumroad | Neubrutalism |
| Scrapbook | Layered paper, tape, torn edges, stickers, handwriting, collage | Personal, crafty, warm | ? Dego Interactive (cited by designmodo) | Scrapbook |
| Surrealism | Dreamlike impossible scenes, odd scale, objects in the wrong places | Uncanny, poetic, curious | ? "Awwwards surreal website" | Surrealism |
| Y2K Aesthetic | Chrome, bubbles, translucent plastic, iridescence, futurism as imagined in 1999–2004 | Shiny, optimistic, retro-future | ✓ iMac G3; "Winamp skins" | Y2K_Futurism |
| Pixel Art | Low-res grid graphics, bitmap fonts, limited palette | Nostalgic, gamey, charming | ✓ Stardew Valley; Celeste | 8-Bit |
| Synthwave | 80s neon: sunset gradients, chrome text, grid horizon, magenta and cyan | Retro, nocturnal, cinematic | ✓ Far Cry 3: Blood Dragon; Kung Fury | Synthwave |
| Glassmorphism | Frosted translucent panels (backdrop blur) over color, thin light borders | Airy, modern, layered | ✓ macOS Big Sur; Apple visionOS | Glassmorphism |
| Neumorphism | Same-color surfaces raised or pressed in with paired light and dark shadows | Soft, calm, minimal | ✓ "Skeuomorph Mobile Banking" by Alexander Plyuto (Dribbble) | Neumorphism |
| Bento Grid | Content in a tidy grid of rounded tiles of mixed sizes | Organized, scannable, product-y | ✓ Apple iPhone product page feature grids | Bento_Grid |
| Editorial Design | Magazine layout: strong headlines, columns, pull quotes, big imagery | Considered, literate, story-led | ✓ NYT "Snow Fall"; The Pudding | Editorial_Magazine_Layout |
| Swiss Design | International Typographic Style: strict grid, sans-serif, asymmetry, clarity | Rational, precise, timeless | ✓ Vignelli NYC subway map; "Swissted" posters | International_Typographic_Style |
| Minimalism | Few elements, lots of white space, a restrained palette | Quiet, focused, premium | ✓ Apple; Muji | Minimalism |
| Maximalism | More is more: pattern on pattern, saturated color, dense layering | Bold, joyful, overwhelming | ? Gucci website (Alessandro Michele era) | Maximalism |
| Luxury Typography | High-contrast serifs (Didot, Bodoni), generous space, black/ivory/gold | Elegant, expensive, editorial | ✓ Harper's Bazaar and Vogue mastheads | ≈ Quiet_Luxury |
| Conceptual Sketch | Hand-drawn lines, wobbly boxes, marker notes, unfinished on purpose | Exploratory, informal, honest | ✓ Excalidraw; Balsamiq | ≈ Hand_Drawn |
| Ethereal | Pastel haze, blur, soft glow, light diffusion | Dreamy, gentle, otherworldly | ? Calm (app) | Ethereal |
| Bohemian | Earthy warm tones, florals, macramé textures, eclectic mix | Free-spirited, warm, artisan | ✓ Anthropologie; Free People | ≈ Geo-Boho |
| Victorian | Ornate borders, filigree, woodcut images, dense serif type, every surface filled | Formal, antique, theatrical | ? "Victorian web design Dribbble" | Victorian |
| Cyberpunk | Neon on dark city grime, glitch, HUD (heads-up display) overlays, warning yellows | Edgy, dystopian, high-tech | ✓ Cyberpunk 2077 | Cyberpunk |
| Wabi-Sabi | Beauty in imperfection: muted earth tones, natural texture, asymmetry, emptiness | Calm, humble, grounded | ✓ Kinfolk magazine; Aesop | Wabi-Sabi |

## Build cues (one line each)
- **Claymorphism**: radius 24–40px; outer drop shadow + two inset shadows (light top-left, dark bottom-right); pastel fills; rounded sans (Nunito, Fredoka).
- **Cybercore**: black ground; neon green/cyan; monospace + pixel display font; scan lines, wireframe/globe SVG, binary strings.
- **Neo-Brutalism**: 3px black borders; `box-shadow: 6px 6px 0 #000`; flat yellow/pink/blue; bold grotesk (Space Grotesk, Archivo Black); buttons shift on press.
- **Scrapbook**: paper textures (CSS noise), slight rotations, tape strips, handwritten font (Caveat) + typewriter; overlapping cards.
- **Surrealism**: one impossible hero image (SVG): floating objects, wrong scale, sky inside shapes; serif display; calm layout so the strangeness reads.
- **Y2K Aesthetic**: chrome and iridescent gradients, bubble buttons, translucent plastic panels, star sparkles; rounded techno font (Orbitron sparingly).
- **Pixel Art**: `image-rendering: pixelated`; 8–16 color palette; bitmap font (Press Start 2P for headings only, readable body); hard-edged boxes.
- **Synthwave**: deep purple → magenta → orange sunset; perspective grid floor; chrome/neon headline with glow; cyan accents.
- **Glassmorphism**: vivid blurred background blobs; panels `backdrop-filter: blur(16px)`, white 10–20% fill, 1px white/30% border; keep text on solid enough fill.
- **Neumorphism**: one base color; raised = light + dark outer shadows, pressed = inset; add a real accent color and borders where needed for contrast.
- **Bento Grid**: CSS grid, mixed tile spans (2×1, 1×2), 16–24px gaps, rounded 20px tiles, one idea per tile.
- **Editorial Design**: serif headlines (Playfair, Fraunces), multi-column body, drop cap, pull quote, captions, rules between sections.
- **Swiss Design**: 12-column grid, flush-left ragged-right, Helvetica-like sans (Inter, Archivo), red/black/white, big numerals, asymmetric balance.
- **Minimalism**: one typeface, two weights; one accent; space does the separating, not lines or boxes.
- **Maximalism**: layered patterns, 4+ saturated colors, mixed fonts, stickers/shapes, but a clear reading path.
- **Luxury Typography**: Didot/Bodoni display (Playfair Display, Bodoni Moda), tracked small caps, ivory/black, thin gold rules, wide margins.
- **Conceptual Sketch**: rough SVG strokes (hand-drawn wobble), marker font (Kalam, Patrick Hand), grid paper, sticky-note callouts, grayscale + one marker color.
- **Ethereal**: pastel radial gradients, blurred orbs, soft glow, thin light serif; raise text contrast with a darker ink color.
- **Bohemian**: terracotta, ochre, sage, cream; floral/geometric pattern borders; serif + script accent; woven textures.
- **Victorian**: ornamental frames (SVG filigree), oxblood/forest/gold, blackletter or Victorian display headline + old-style serif body, engraving-style images.
- **Cyberpunk**: near-black with neon pink/cyan/yellow, glitch offsets, angled clipped corners, HUD brackets, condensed techno font (Rajdhani, Oxanium).
- **Wabi-Sabi**: stone/clay/linen palette, paper grain, irregular blob shapes, lots of empty space, soft serif; nothing perfectly aligned that doesn't need to be.
