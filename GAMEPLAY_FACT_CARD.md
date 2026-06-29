# Mill By Moonlight - Gameplay Fact Card

## App Identity
- **App Name**: Mill By Moonlight
- **Bundle ID**: com.rosewood.millbymoonlight.game
- **Version**: 1.0
- **Platform**: iOS (iPhone only)
- **Minimum iOS**: 15.0
- **Framework**: SpriteKit + Objective-C
- **Orientation**: Portrait only
- **Age Rating**: 4+
- **Network**: Fully offline, no ads, no IAP, no analytics, no tracking

## Core Gameplay Loop
1. A contract begins at the Eling tide mill with a day limit (15-30 game days).
2. The moon phase advances each day, driving tide amplitude (spring/neap cycle).
3. When the moon is at least one-third full, tap the millstone to engage grinding.
4. Wheat is consumed and flour is produced based on tide energy and millstone efficiency.
5. Sell flour for gold to free storage and earn income.
6. Upgrade water wheel, millstone, or storage for better performance.
7. Reach the flour or gold target before the day limit to complete the contract.

## Mills and Equipment
**Millstone Types** (4): Stone (0.70), Porcelain (0.85), Steel (0.95), Ceramic (0.90).

**Upgrade Tracks** (3):
- Water Wheel: 30 gold/level (improves tide energy capture)
- Millstone: 40 gold/level (improves grinding efficiency)
- Storage: 25 gold/level (+10 capacity per level)

**Moon Phases** (8): New Moon, Waxing Crescent, First Quarter, Waxing Gibbous, Full Moon, Waning Gibbous, Last Quarter, Waning Crescent.

**Tide Model**: `amplitude = baseTideRange × (0.35 + 0.65 × sin(moonPhase × π))`, with half-day cycles and weather disturbance.

## Level Progression
- **Total Levels**: 50
- **Location**: Eling, Hampshire, UK (historic tide mill)
- **3 Contract Types**:
  - Production: reach target flour amount
  - Time Limit: complete within 15 or 20 days
  - Comprehensive: reach both flour and gold targets

**Millstone Eras**:
1. Stone Era (Levels 1-10): Stone millstone, single wheel
2. Porcelain Era (Levels 11-30): Porcelain millstone, single/double wheel
3. Steel Era (Levels 31-40): Steel millstone, double wheel
4. Ceramic Era (Levels 41-50): Ceramic millstone, double wheel

- **Unlock**: Linear; completing level N unlocks level N+1 (NSUserDefaults key: `tm_level{N}_unlocked`).
- **Stars**: Stored per level (NSUserDefaults key: `tm_level{N}_stars`).

## Scoring (per contract)
- **Flour Score** (40 points): min(1.0, actual/target) × 40
- **Gold Score** (30 points): min(1.0, actual/target) × 30 (or 100G baseline)
- **Upgrade Score** (30 points): min(1.0, upgrades/5) × 30
- **Total**: 0-100

## Star Rating
- 3 stars: score >= 80
- 2 stars: score >= 60
- 1 star: score >= 40
- 0 stars: score < 40 (failed, but can retry)

## Game Mechanics
- **Time**: 1 second real = 1 game day; contracts last 15-30 days
- **Moon Phase**: 30-day lunar cycle, advances 1/30 per day
- **Tide Energy**: Requires moon phase >= 1/3 to engage millstone; auto-disengages below
- **Milling Formula**: `output = feedRate × 0.5 × springFactor × millstoneEfficiency × levelSpeed × dualMillstoneFactor(1.8)`
- **Feed Rate**: Adjustable 1-10
- **Market Price**: Fixed 5G base in early levels; fluctuates 3-8G in later levels (level 23+)

## Monetization
- None. No ads, no in-app purchases, no subscriptions.

## Data Collection
- None. All progress saved locally via NSUserDefaults.

## Template Residue Check
- No tw_*, game_01_*, Template, or other template residue found.

## Debug UI
- showsFPS: Not set (default NO)
- showsNodeCount: Not set (default NO)
- prefersStatusBarHidden: YES
