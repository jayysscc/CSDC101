#include <iostream>
#include <string>

// Global variables for tracking character states and relationships
bool isMerciful = false;  // Tracks if Robert chose mercy in the interrogation
int Blazer_Impression_Score = 0;  // Tracks Blonde Blazer's impression (higher = more memorable/chaotic)
bool isRomanticTensionActive = false;  // Tracks if romantic tension is active after the billboard scene
int Robert_Efficiency_Rating = 0;  // Additional variable: Tracks Robert's tactical efficiency (increases with smart choices, affects epilogue)

// Function prototypes
void scene_interrogation();
void scene_street_fight();
void scene_bar_flambae();
void scene_billboard();
void scene_combat_toxic();
void epilogue_summary();

int main() {
    std::cout << "Welcome to Robert's Pivot: A Text-Based Visual Novel based on Dispatch.\n";
    std::cout << "Your choices will shape Robert's journey from superhero to dispatcher.\n\n";

    // Call scenes in sequence
    scene_interrogation();
    scene_street_fight();
    scene_bar_flambae();
    scene_billboard();
    scene_combat_toxic();
    epilogue_summary();

    return 0;
}

// Scene 1: The Moral Crossroads - Apartment Interrogation
void scene_interrogation() {
    std::cout << "\n--- Scene: Apartment Interrogation ---\n";
    std::cout << "You're Robert, interrogating the Soothing Goon who's dangling from the building.\n";
    std::cout << "Do you pull him back to safety (1) or let him drop (2)?\n";
    int choice;
    std::cin >> choice;

    if (choice == 1) {
        std::cout << "You pull him back. He spills the info out of fear and gratitude. Mercy prevails.\n";
        isMerciful = true;
    } else if (choice == 2) {
        std::cout << "You let him drop. The fall silences him permanently. Efficiency at any cost.\n";
        isMerciful = false;
    } else {
        std::cout << "Invalid choice. Defaulting to mercy.\n";
        isMerciful = true;
    }
}

// Scene 2: Tactical Consequence - Street Fight
void scene_street_fight() {
    std::cout << "\n--- Scene: Street Fight ---\n";
    std::cout << "A thug swings a crowbar at you. Quick decision: Right hand punch (1) or left hand punch (2)?\n";
    int choice;
    std::cin >> choice;

    if (choice == 1) {
        std::cout << "You punch with your right hand. He counters, striking you with the crowbar. Game Over - you're down!\n";
        std::cout << "(This failure highlights tactical consequences. Restarting scene for narrative flow.)\n";
        Robert_Efficiency_Rating -= 1;  // Penalty for poor choice
    } else if (choice == 2) {
        std::cout << "You punch with your left hand. Perfect timing - he's knocked out. Tactical win!\n";
        Robert_Efficiency_Rating += 1;  // Bonus for smart choice
    } else {
        std::cout << "Invalid choice. Defaulting to success.\n";
        Robert_Efficiency_Rating += 1;
    }
}

// Scene 3: Relationship Impact - The Superhero Bar Scene
void scene_bar_flambae() {
    std::cout << "\n--- Scene: Superhero Bar with Flambae ---\n";
    std::cout << "Flambae's on fire! Throw water (1) to extinguish or alcohol (2) to amplify?\n";
    int choice;
    std::cin >> choice;

    if (choice == 1) {
        std::cout << "You throw water. Flames die down, but Flambae looks subdued and in pain. Subtle approach.\n";
        Blazer_Impression_Score += 1;  // Mild impression
    } else if (choice == 2) {
        std::cout << "You throw alcohol. Fire explodes! Chaos ensues, and Blonde Blazer notices your boldness.\n";
        Blazer_Impression_Score += 3;  // Strong impression
    } else {
        std::cout << "Invalid choice. Defaulting to water.\n";
        Blazer_Impression_Score += 1;
    }
}

// Scene 4: Romance Route - Billboard Scene
void scene_billboard() {
    std::cout << "\n--- Scene: Billboard with Blonde Blazer ---\n";
    std::cout << "The moment hangs. Kiss her (1) or let the moment pass (2)?\n";
    int choice;
    std::cin >> choice;

    if (choice == 1) {
        std::cout << "You kiss her. Vulnerability opens romance possibilities.\n";
        isRomanticTensionActive = true;
    } else if (choice == 2) {
        std::cout << "You let it pass. Tension lingers without commitment. Emotional intelligence shines.\n";
        isRomanticTensionActive = false;
    } else {
        std::cout << "Invalid choice. Defaulting to letting it pass.\n";
        isRomanticTensionActive = false;
    }
}

// Scene 5: Character Reflection - Combat Decision
void scene_combat_toxic() {
    std::cout << "\n--- Scene: Combat with Toxic ---\n";
    std::cout << "Toxic's down. Punt him off the building (1) or stomp for efficiency (2)?\n";
    int choice;
    std::cin >> choice;

    if (choice == 1) {
        std::cout << "You punt him. Flashy and creative - comic relief!\n";
        if (isMerciful) {
            std::cout << "(Your merciful nature makes this feel like a warning, not a kill.)\n";
        }
    } else if (choice == 2) {
        std::cout << "You stomp. Brutal and efficient - intimidation tactic.\n";
        if (!isMerciful) {
            std::cout << "(Your ruthless streak shines through in this no-nonsense finish.)\n";
        }
    } else {
        std::cout << "Invalid choice. Defaulting to punt.\n";
        if (isMerciful) {
            std::cout << "(Mercy influences your creative choice.)\n";
        }
    }
}

// Epilogue: Summary based on variables
void epilogue_summary() {
    std::cout << "\n--- Epilogue: Robert's Pivot ---\n";
    std::cout << "Reflecting on your choices, Robert's arc unfolds:\n";

    if (isMerciful) {
        std::cout << "Your merciful path leads to compassionate leadership as a dispatcher.\n";
    } else {
        std::cout << "Your pragmatic efficiency forges a reputation for ruthless results.\n";
    }

    if (Blazer_Impression_Score >= 3) {
        std::cout << "Blonde Blazer remembers your chaotic, memorable actions vividly.\n";
    } else {
        std::cout << "Blonde Blazer recalls your actions as subtle and forgettable.\n";
    }

    if (isRomanticTensionActive) {
        std::cout << "Romantic tension with Blonde Blazer sparks future possibilities.\n";
    } else {
        std::cout << "Romantic tension remains unresolved, preserving emotional distance.\n";
    }

    if (Robert_Efficiency_Rating > 0) {
        std::cout << "Your tactical smarts prepare you well for behind-the-scenes strategy.\n";
    } else {
        std::cout << "Tactical missteps highlight the need for a pivot to dispatching.\n";
    }

    std::cout << "\nEnd of Robert's Pivot. Thanks for playing!\n";
}
