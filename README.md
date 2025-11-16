import random
import textwrap

def generate_art_prompt(subject: str, brand_name: str | None = None) -> str:
    subject = subject.strip() or "a product"
    style = random.choice([
        "minimalist flat illustration",
        "3D semi-realistic render",
        "futuristic cyberpunk artwork",
        "hand-drawn sketch style",
        "bold geometric poster design",
        "luxury editorial photography style",
        "isometric illustration",
        "vintage retro poster",
        "neon glow vaporwave style",
        "soft pastel aesthetic"
    ])
    medium = random.choice([
        "digital illustration",
        "poster design",
        "social media cover",
        "product hero shot",
        "branding key visual",
        "UI hero banner"
    ])
    mood = random.choice([
        "energetic and bold",
        "calm and elegant",
        "luxurious and premium",
        "playful and fun",
        "dark and dramatic",
        "bright and optimistic"
    ])
    palette_hint = random.choice([
        "using rich dark backgrounds with one strong accent color",
        "using pastel tones with soft contrast",
        "using high-contrast complementary colors",
        "using monochrome with a single neon highlight",
        "using warm sunset colors",
        "using cold futuristic blue and cyan tones"
    ])
    lighting = random.choice([
        "soft cinematic lighting",
        "hard studio lighting with sharp shadows",
        "glowing backlight and rim light",
        "top-down soft light",
        "moody low-key lighting"
    ])
    perspective = random.choice([
        "front view",
        "3/4 perspective view",
        "top-down flat lay",
        "slight low-angle hero shot",
        "isometric perspective"
    ])
    details = random.choice([
        "clean empty background, focus on the subject",
        "subtle gradients and soft glow around the main subject",
        "abstract geometric shapes in the background",
        "glassmorphism cards and floating UI elements",
        "light particles and bokeh in the background",
        "futuristic lines and HUD details"
    ])

    brand_part = f" for the brand '{brand_name}'" if brand_name else ""
    prompt = f"""
    Create a {medium}{brand_part}.
    Subject: {subject}.
    Style: {style}, {mood}.
    Color: {palette_hint}.
    Composition: {perspective}, {details}.
    Lighting: {lighting}.
    Output: ultra sharp, high resolution, perfect for Instagram and posters.
    """
    return textwrap.dedent(prompt).strip()


def generate_color_palette():
    palettes = [
        {
            "name": "Sunset Neon",
            "colors": ["#0B0B2E", "#3A0CA3", "#F72585", "#FF8500", "#FFBE0B"],
        },
        {
            "name": "Soft Pastel",
            "colors": ["#FFE5EC", "#FFC2D1", "#FFB3C6", "#8E9AAF", "#B8C0FF"],
        },
        {
            "name": "Luxury Gold",
            "colors": ["#050505", "#121212", "#8D7633", "#D4AF37", "#F5E6C5"],
        },
        {
            "name": "Clean Minimal",
            "colors": ["#FFFFFF", "#F4F4F4", "#E0E0E0", "#111827", "#3B82F6"],
        },
        {
            "name": "Cyber Blue",
            "colors": ["#020617", "#0F172A", "#0EA5E9", "#22D3EE", "#A855F7"],
        },
    ]
    chosen = random.choice(palettes)
    return chosen

def main():
    print("🎨 Art & Design Helper")
    print("----------------------")
    print("1) Generate AI image prompt")
    print("2) Generate random color palette")
    choice = input("Choose 1 or 2: ").strip()

    if choice == "1":
        subject = input("Describe your subject (e.g., 'a leather travel suitcase in a shop'): ")
        brand = input("Brand name (optional, press Enter to skip): ").strip() or None
        prompt = generate_art_prompt(subject, brand)
        print("\n🔧 Copy this prompt into your AI image tool:")
        print("-" * 60)
        print(prompt)
        print("-" * 60)
    elif choice == "2":
        palette = generate_color_palette()
        print("\n🎨 Color Palette:", palette["name"])
        for i, c in enumerate(palette["colors"], start=1):
            print(f"{i}. {c}")
        print("\nUse these hex codes in Canva / Figma / Photoshop.")
    else:
        print("Invalid choice. Please run again and choose 1 or 2.")


if __name__ == "__main__":
    main()

