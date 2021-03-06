# Changelog

## [2.0]

Celebrating the 100th Patreon supporter, the modules from Virtual Tabletop Assets will be released on public repositories, and the Chrome extension will be made available on the Chrome Web Store - along with delayed release cycles and manually timed releases between the Chrome extension and the campanion module vtta-dndbeyond, let's see how that works out.

This marks some major changes that are now possible:

- Publicly viewable issue trackers
- Possibility to work with the community on changes, like accepting changes
- In general, a broader availability of my modules

The Chrome extension will be working in two modes:

- "Basic mode" allows the import of everything covered by the SRD, or marked "Basic Rules" on D&D Beyond
- "Patreon mode" allows the import of everything else on top.

In the spirit of Dungeons & Dragons, this will make the toolset available for a rather large portion of the available content on D&D Beyond and likewise, making it possible for a broader audience to make use of these tools free of charge.

For patreon will be a lot in store in the future, and now even: Importing all monsters, including homebrew variants as long as they are parseable by following the official formatting (or at least do not stray further than the official monsters do), and eventually adventure module export - yeah, great news, I have some nifty ideas on how to tackle that and this will be on the roadmap for 2020.

### Fixed

- Cleaned the flags up and provided correct namespacing (yeah, I do claim vtta as a namespace for me ;)

### Added

- When importing Monsters, subfolders according to monster type will be created to organize the imports a little bit better. Thanks for the suggestion, @sky

## [1.1.1]

### Fixed

- Character import updates the item and spell compendium now correctly again
- Initative values for monster imports were calculated correctly, but would be account to twice when Foundry created the entity, this is now corrected

### Changed

- Changed the seperator for proficiencies from comma to semicolon in order to have nicer labels on the default DND5e character sheeet

## [1.1]

### Added

- Compatibility for Foundry VTT v0.4.4 and higher
- Enabling or disable via CONFIG: `CONFIG.debug.vtta.dndbeyond = <object>` enables or disables debug logging in the console.log for certain sections of the module:

  dndbeyond.basic: TRUE|FALSE, // general logging
  dndbeyond.messaging: TRUE|FALSE, // regarding communication between components
  dndbeyond.character: TRUE|FALSE, // regarding character import
  dndbeyond.extension: TRUE|FALSE // regarding extension imports/ additions to the world

### Removed

- Compatibility for Foundry VTT v0.4.3 and lower

### Fixed

- Improved parsing by cleaning &nbsp; from random D&D Beyond markup, replacing them by regular spaces
- [B] Import Button CSS fixes for Foundry VTT v0.4.4, does not react on hitting the Enter key any more

## [1.0.10] Hotfix

### Fixed

- Compendium import was not bugging out if Iconizer was not responding/missing. I want you to use my modules, but I don't want to enforce them that way ;)

### Added

- Supporting Feat "Tough" for Hitpoint calculation

## [1.0.9]

Due to a change in the settings for the module you will need to revisit them. Instead of specifying target compendiums by name, you will select them in a select input, which should yield in lesser errors, especially for newer users. Nevertheless, the old settings will be stored unless you open the settings at least once and select your desired compendiums again.

### Fixed

- Some spells were parsed as ranged attack incorrectly (thanks @n3rf_herder), switched action type to melee spell attack if range is self our touch

- Fixed spell save DC for character imports (thanks @n3rf_herder) which were always based on the character's spellcasting ability instead of the correct ability

- Defaulting weapon properties thrown, finesse, reach to false as intended

- Fixed formula to calculate a modifier based on a value

- Used bundlesize to calculate the real weight of each item in for stacked items (Ball Bearings, I am looking at you)

- Legendary Action count not parsing correctly

- Legendary Action and Resistance current values fixed, set to max values

- Senses, and custom senses are now reflected in the token settings. Truesight and Brightsight refer to "Bright Sight" (Foundry), Darkvision to "Dim Sight" (Foundry). Magical bonuses from items are influencing those values, too, if the item is worn by the character (ref Goggles of Night)

- Fixed two bugs regarding armor class calculation for character imports

- Add only spells to a monster import that are in the sections "Spellcasting" and "Innate Spellcasting", but not in other section as references (see https://www.dndbeyond.com/monsters/acererak, section "Invoke Curse" for an example of spells that are not added any longer)

### Added

- Used [Azzurite's Settings Extender](https://gitlab.com/foundry-azzurite/settings-extender) to simplify configuration

- Feats are now parsed and added to the character's features, too

- Personality Traits, Ideals, Bonds and Flaws are now part of the biography section

### Changed

- Set spell save DC for character imports to be null, e.g. to be based on the current ability values. This enables characters to advance within Foundry and that save value to always be correct (thanks @n3rf_herder)

- Testing: Set the base proficiency for monsters to be 2 in order to avoid strange to hit bonuses for lower (0-1/2) level monsters

- Limited use features are now marked as such and generated as limited use features of the character. In past releases, those were only shown in as primary, secondary and tertiary resources and therefore limited to a maximum of three, now all are shown and accessible, including resets on long or short rests.

- Not setting values for the following token settings on import anymore: brightLight, dimLight, lightAngle, scale

- On monster import, differentiated between chat description without attack details and item description (full details)

## [1.0.8]

### Added

- Rollable buttons on the monster pages: Abilities, Skills and Features/ Actions should now work propery. In order to use and see these buttons, the actor must be added to the current world first. All shortcuts for rolls you know from Foundry are working, so holding SHIFT, CTRL or ALT works as a "Regular ROll", "Disadvanted Roll" and "Advantaged" roll as expected.

### Changed

- If a monster is already present in the current world, the "Add to World" now acts as an update to avoid creating multiple copies of the same actor. If you want to have multiple copies of an actor, please add it once, rename it within Foundry and add it again

### Fixed

- Added support for swarm types that weren't parsing correctly as in terms of "size" (thanks @tposney)
- Fixed a bug in calculating spell slots and cantrips known for multiclassing spellcasters (thanks @Hailot)
- Improved Action parsing (this will be an ongoing process, please report improvable parsings)

## [1.0.7]

- Added size 'huge' to monster parsing (thanks @tposney)

## [1.0.6] - 2019-12-21

- Enhanced compatibility with Beyond20
- Stopping page process on main category pages (/monsters, /spells)

## [1.0.5] - 2019-12-21

- Multiple fixes, patreon-internal release
- Special thanks to @tposney to iron out so many bugs before anyone else was bothered by it

## Fixed

- Race condition asking iconizer for icons, now import goes on if iconizer is not responding in a timely manner

- Character import was malfunctioning after refactoring, this is fixed now

## [1.0.4] - 2019-12-20

### Added

- Monster import

### Changed

- Image upload changed from 'source = user' to 'source = data' to upload to user data directory, resulting in a 0.4.2 requirement of Foundry VTT
- Removed ability to choose to not import entities at all, after all this is what this module really is about

## [1.0.3b] - 2019-12-10

### Fixed

- Added missing ability modifiers for weapon attacks

## [1.0.3] - 2019-12-10

### Added

- Added Cantrip- (implemented in Foundry 0.4.1) and Spell-Scaling (currently not yet implemented in Foundry 0.4.1)
- Added Unarmed Attack for Monks (DEX or STR based attack plus Monk Martial Arts die). While Unarmed Strikes are displayed on the character sheet for every character, it is within the JSON for Monks available only

### Fixed

- Spell preparation mode was not working as intended (thanks @Alamaise and @nerf_herder)
- Allowing dashes (`-`) and underscores (`_`) in the D&D Beyond username now, too (thanks @Alamaises)

### Changed

- Changed the spell preparation mode for several classes from "always" to "prepared" in order to show spell slots for those classes. This change can be reversed once the GUI for the default character sheet shows spell slots even for spells that do not need preparing

## [1.0.2] - 2019-21-11

### Added

- Token configuration with vision settings

### Fixed

- D&D Beyond button color indication (correct D&D Beyond Character URL set: red, otherwise white-ish)

## [1.0.1] - 2019-20-11

### Added

- Indicators for user feedback on setting the D&D Beyond URL

### Fixed

- Parsing of Wondrous Items was not detected correctly
- Description of features was added incorrectly to the corresponding item
- CSS fix for the D&D Beyond button
- Integrated the functionality of DDBPopper into this module, thanks @errational for suggesting to join forces

### Changed

- The key modifier for opening the D&D Beyond Charactersheet is how SHIFT, was: CTRL
- Set the application name instead of displaying it as a header

## [1.0.0] - 2019-20-11

### Added

- Initial release

### Removed

- Support for Foundry v0.3.9 and prior
