# Spec Delta

## Purpose

A chalkboard real-time strategy game where the player hires workers,
hatches soldiers, and rushes the enemy castle while a rival general
marches back — simple economy, auto-battling chalk armies, and one big
RUSH lever, all drawn like a general's war-room board.

## ADDED Requirements

### Requirement: Gather-and-rush economy
The app SHALL generate energy for the player from hired workers each
second, SHALL spend that energy on hiring more workers or hatching
soldiers at clear prices, and SHALL refuse purchases the player cannot
afford with a friendly message.

#### Scenario: Workers gather energy
- **WHEN** the battle is running and the player has workers on the board
- **THEN** energy rises over time, faster with more workers

#### Scenario: Affordable purchase
- **WHEN** the player presses hire or hatch with enough energy
- **THEN** energy is spent and the new unit joins the player's side

#### Scenario: Too expensive
- **WHEN** the player presses a purchase without enough energy
- **THEN** nothing is bought and a message explains it

### Requirement: Command levers
The app SHALL provide three command levers: hire a worker, hatch a
soldier, and RUSH. RUSH SHALL boost every friendly soldier's speed and
damage for a short time, then rest on a cooldown the player can see.

#### Scenario: Hire and hatch levers
- **WHEN** the player pulls the hire or hatch lever
- **THEN** a worker or soldier stamp appears on the player's side

#### Scenario: Rush surge
- **WHEN** the player pulls the RUSH lever
- **THEN** all friendly soldiers charge faster and hit harder until the surge ends, and the lever shows a cooldown

### Requirement: Auto-battling armies
The app SHALL march each soldier toward the enemy castle, have soldiers
stop and fight nearby enemies first, damage the enemy castle when they
arrive, and remove units whose health reaches zero.

#### Scenario: March and fight
- **WHEN** a soldier meets an enemy soldier on the way
- **THEN** both stop and trade hits until one falls

#### Scenario: Siege the castle
- **WHEN** a soldier reaches the enemy castle with no enemies in the way
- **THEN** the soldier damages the castle on each attack

#### Scenario: Fallen units
- **WHEN** a unit's health reaches zero
- **THEN** it leaves the board in a puff of chalk dust

### Requirement: Rival general
The app SHALL run an enemy commander that gains its own energy, hires
workers, and hatches soldiers on its own, growing tougher as the battle
runs longer.

#### Scenario: Enemy economy
- **WHEN** the battle runs
- **THEN** the rival's energy and army grow on their own over time

#### Scenario: Enemy pressure
- **WHEN** the rival can afford soldiers
- **THEN** enemy soldiers march toward the player's castle

### Requirement: Win, lose, and records
The app SHALL end the battle with a victory screen when the enemy castle
falls and a defeat screen when the player's castle falls. It SHALL save
the best (lowest) win time and the best win streak in local storage,
update them only when better, show a NEW BEST banner on improvement, and
keep them across reloads. Save failures SHALL NOT break the game.

#### Scenario: Victory
- **WHEN** the enemy castle's health reaches zero
- **THEN** a victory screen shows the win time and streak

#### Scenario: Defeat
- **WHEN** the player's castle's health reaches zero
- **THEN** a defeat screen shows and the win streak resets

#### Scenario: New best
- **WHEN** a win beats the saved best time or streak
- **THEN** the improved record is saved and a NEW BEST banner appears

#### Scenario: Reload keeps records
- **WHEN** the page is reloaded after a record is saved
- **THEN** the same best time and streak are shown

### Requirement: Chalk war-room presentation
The app SHALL render a dusty chalkboard with chalk-stroke castles, stick
soldier stamps, marching dust, scribbled fight sparks, chalk surge
arrows during RUSH, and wooden-lever buttons, all drawn in code with zero
image assets.

#### Scenario: Launch look
- **WHEN** the app loads
- **THEN** the chalkboard, castles, and levers are drawn with no image files used

### Requirement: Battle flow and recovery
The app SHALL flow from a ready screen into the battle and on to the
victory or defeat screen, with a play-again action that resets the board
to a fresh battle. A clear-records action SHALL reset saved records and
confirm with a toast.

#### Scenario: Play again
- **WHEN** the player takes the play-again action from a result screen
- **THEN** a fresh battle starts with both castles and economies reset

#### Scenario: Clear records
- **WHEN** the player presses the clear-records action
- **THEN** saved records reset and a toast confirms it
