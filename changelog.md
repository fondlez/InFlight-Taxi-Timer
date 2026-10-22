# Changelog for "InFlight Taxi Timer"

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.1] - 2026-10-22

### Fixed
- Fixed flight timer continuing to record and never stopping after landing. Replaced unreliable `UNIT_AURA` and `MINIMUM_FLIGHT_SPEED` checks with direct `UnitOnTaxi` polling (with a grace window) and `PLAYER_CONTROL_GAINED`.
- Fixed flights occasionally failing to be detected by adding `PLAYER_CONTROL_LOST` and `PLAYER_ENTERING_WORLD` event hooks with `StartTaxiFlight` and `CheckPendingTaxi` fallbacks.
- Fixed Lua error for Neutral faction (Pandaren) by initializing `Neutral` in `InFlightVars`.
- Fixed nil error when calling `GetGuildLevel` by ensuring `IsInGuild()` is checked before querying guild level.
- Added safety checks for `CanExitVehicle` and `Dismount`.

## [1.0.0] - 2025-01-15

Initial upload.

### Added
- README.md
- changelog.md

### Changed
- added an alternate event to detect the end of flights in case the existing
event was not fired
