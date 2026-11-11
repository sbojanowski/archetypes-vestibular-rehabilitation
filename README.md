# Vestibular Rehabilitation OpenEHR Archetypes

## Archetype Claude Prompts

### Visual Motion Sensitivity VAS Assessment

#### Prompt

Create OpenEHR archetype named visual_motion_sensitivity based on Observation OpenEHR reference model class containing 7 assessment  items for Visual Motion Sensitivity assessment performed using Virtualis Visual Motion Sensitivity virtual reality application. Items in the assessment are as following:
1. "Optokinetic - motionless" - of Quantity type, in form of VAS from 0 to 10,
2. "Optokinetic - movement to the left" - of Quantity type, in form of VAS from o to 10,
3. "Optokinetic - movement to the right" - of Quantity type, in form of VAS from 0 to 10,
4. "Optokinetic - upward movement" - of Quantity type, in form of VAS from 0 to 10,
5. "Optokinetic - downward movement" - of Quantity type, in form of VAS from 0 to 10,
6. "Optical flow - motionless" - of Quantity type, in form of VAS from 0 to 10,
7. "Optical flow - forward direction" - of Quantity type, in form of VAS from 0 to 10,
8. "Optical flow - backward direction" - of Quantity type, in form of VAS from 0 to 10.
Create OpenEHR template for Visual Motion Sensitivity named Visual_Motion_Sensitivity based on Encounter, containing Visual Motion Sensitivity assessment an the only encounter item.