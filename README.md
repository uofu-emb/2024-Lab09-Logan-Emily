# 2024-Lab09-Logan-Emily

## Invariants
- An approach signal will always preceed a depart signal
- The power will never be interrupted
- Trains on each track only run in one direction
- There will only ever be one train occupying an approach/depart signal at one time
- There will only every be one train in the intersection per track at one time
- A second approach signal won't occur on the same track until the depart signal for the first train on that track clears (this is going off of the assumption that there's some appropriate spacing between back to back trains on the same track)
- A train will always either be long enough or be traveling slow enough that 10 seconds will always elapse before the depart signal is triggered after the apprach signal is sent (for the same track)
- If the alarm is on, it is ringing (i.e. it makes sound and works properly)

## Varying Invariants
- If the FSM sequence begins due to an approach on one track, if a second approach begins on the other track while the sequence is already started, then it gets ignored and the safety mechanism (gates down and alarm on) turn off early due to the first train hitting depart while the second train is still in the system. In othe words, this system does not account for the fact that a second train can eneter the system at any point which requires some additional control mechanisms to ensure the FSM stays active for the appropriate duration.

## FSM Partner Checking
- For Emily:
  - She had the 10 second elapsed signal misplaced on one of the state transitions.
- For Logan:
  - Add an invariant that given the train length and/or travel speed, that the 10 second timer always triggers the elapsed signal before the depart signal can ever be sent.

## Prove It
| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | ringing | safety_hazard | next state |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|------------|
| 0      | 0         | 0        | 0                  | 0                  | 0              | 0              | 0            | 0            | 0       |               |            |
| 1      | 0         | 0        | 0                  | 1                  | 0              | 1              | 0            | 0            | 0       |               |            |
| 2      | 0         | 0        | 1                  | 0                  | 1              | 0              | 0            | 0            | 0       |               |            |
| 3      | 0         | 0        | 1                  | 1                  | 1              | 1              | 0            | 0            | 0       |               |            |
| 4      | 0         | 1        | 0                  | 0                  |                |                |              |              |         |               |            |
| 5      | 0         | 1        | 0                  | 1                  |                |                |              |              |         |               |            |
| 6      | 0         | 1        | 1                  | 0                  |                |                |              |              |         |               |            |
| 7      | 0         | 1        | 1                  | 1                  |                |                |              |              |         |               |            |
| 8      | 1         | 0        | 0                  | 0                  |                |                |              |              |         |               |            |
| 9      | 1         | 0        | 0                  | 1                  |                |                |              |              |         |               |            |
| 10     | 1         | 0        | 1                  | 0                  |                |                |              |              |         |               |            |
| 11     | 1         | 0        | 1                  | 1                  |                |                |              |              |         |               |            |
| 12     | 1         | 1        | 0                  | 0                  |                |                |              |              |         |               |            |
| 13     | 1         | 1        | 0                  | 1                  |                |                |              |              |         |               |            |
| 14     | 1         | 1        | 1                  | 0                  |                |                |              |              |         |               |            |
| 15     | 1         | 1        | 1                  | 1                  |                |                |              |              |         |               |            |

| number | invariant |
|--------|-----------|
| 16     | An approach signal will always preceed a depart signal |
| 17     | The power will never be interrupted |
| 18     | Trains on each track only run in one direction |
| 19     | There will only ever be one train occupying an approach/depart signal at one time |
| 20     | There will only every be one train in the intersection per track at one time |
| 21     | A second approach signal won't occur on the same track until the depart signal for the first train on that track clears (this is going off of the assumption that there's some appropriate spacing between back to back trains on the same track) |
| 22     | A train will always either be long enough or be traveling slow enough that 10 seconds will always elapse before the depart signal is triggered after the apprach signal is sent (for the same track) |
| 23     | If the alarm is on, it is ringing (i.e. it makes sound and works properly) |
