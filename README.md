# Vestibular Rehabilitation OpenEHR Archetypes

## Common assessment item structure

OBSERVATION  openEHR-EHR-OBSERVATION.<your_assessment>.v0
└─ data: HISTORY
   └─ events: EVENT  (time = when the assessment was done)
      └─ data: ITEM_TREE
         ├─ ELEMENT "Assessment status"   DV_CODED_TEXT  [0..1]
         │     local codes: performed | not performed | partially performed
         ├─ ELEMENT "VAS score"           DV_QUANTITY    [0..1]
         │     property: Qualified real, units "1", range 0..10, precision 0 or 1
         └─ ELEMENT "Comment"             DV_TEXT        [0..1]

## Archetype Claude Prompts


### Visual Motion Sensitivity VAS Assessment

#### Prompt
Create OpenEHR archetype named visual_motion_sensitivity based on Observation OpenEHR reference model class containing 7 assessment  items for Visual Motion Sensitivity assessment performed using Virtualis Visual Motion Sensitivity virtual reality application. Items in the assessment are as following:
1. Optokinetic - motionless
2. Optokinetic - movement to the left
3. Optokinetic - movement to the right
4. Optokinetic - upward movement"
5. Optokinetic - downward movement
6. Optical flow - motionless
7. Optical flow - forward direction
8. Optical flow - backward direction
For each assessment item use this OpenEHR structure:
OBSERVATION  openEHR-EHR-OBSERVATION.<your_assessment>.v0
└─ data: HISTORY
   └─ events: EVENT  (time = when the assessment was done)
      └─ data: ITEM_TREE
         ├─ ELEMENT "Assessment status"   DV_CODED_TEXT  [0..1]
         │     local codes: performed | not performed | partially performed
         ├─ ELEMENT "VAS score"           DV_QUANTITY    [0..1]
         │     property: Qualified real, units "1", range 0..10, precision 0 or 1
         └─ ELEMENT "Comment"             DV_TEXT        [0..1]
Create OpenEHR template for Visual Motion Sensitivity named PVR_Visual_Motion_Sensitivity based on Encounter, containing Visual Motion Sensitivity assessment an the only encounter item.

### CrowdVR VAS Assessment

#### Prompt
Create OpenEHR archetype named crowd_vr_assessment based on Observation OpenEHR reference model class containing 6 assessment items for CrovdVR assessment performed using Virtualis CrowdVR virtual reality application. Items in the assessment are as following:
1. Shop environment
2. Narrow corridor environment
3. Shopping center ground floor environment
4. Shopping center first floor environment
5. Metro station environment 
6. City intersection environment
For each assessment item use this OpenEHR structure:
OBSERVATION  openEHR-EHR-OBSERVATION.<your_assessment>.v0
└─ data: HISTORY
   └─ events: EVENT  (time = when the assessment was done)
      └─ data: ITEM_TREE
         ├─ ELEMENT "Assessment status"   DV_CODED_TEXT  [0..1]
         │     local codes: performed | not performed | partially performed
         ├─ ELEMENT "VAS score"           DV_QUANTITY    [0..1]
         │     property: Qualified real, units "1", range 0..10, precision 0 or 1
         └─ ELEMENT "Comment"             DV_TEXT        [0..1]
Create OpenEHR template for CrowdVR Assessment named PVR_Crowd_VR_Assessment based on Encounter, containing Visual Motion Sensitivity assessment an the only encounter item.
