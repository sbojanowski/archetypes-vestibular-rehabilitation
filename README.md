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
Create OpenEHR archetype named crowd_vr_assessment based on Observation OpenEHR reference model class containing 6 items for assessment performed using Virtualis CrowdVR virtual reality application. Items in the assessment are as following:
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
Create OpenEHR template for CrowdVR Assessment named PVR_Crowd_VR_Assessment based on Encounter, containing CrowdVR assessment an the only encounter item.

### EscalatorVR VAS Assessment

#### Prompt
Create OpenEHR archetype named escalator_vr_assessment based on Observation OpenEHR reference model class containing 2 items for assessment performed using Virtualis EscalatorVR virtual reality application. Items in the assessment are as following:
- Observing a moving escalator at low speed
- Observing a moving escalator at high speed
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
Create OpenEHR template for EscalatorVR Assessment named PVR_Escalator_VR_Assessment based on Encounter, containing EscalatorVR assessment as the only encounter item.


# Struktury archetypów

## Video Head Impulse Test (vHIT) – `openEHR-EHR-OBSERVATION.video_head_impulse_test.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.video_head_impulse_test.v1   "Video Head Impulse Test (vHIT)"
├─ data: HISTORY
│  └─ events: POINT_EVENT "Any point in time event"  [0..1]  (time = when the examination was done)
│     ├─ data: ITEM_TREE
│     │  ├─ CLUSTER "Lateral canals"  [0..1]  (HIMP, horizontal plane)
│     │  │  ├─ ELEMENT "Test status"                   DV_CODED_TEXT  [0..1]
│     │  │  │     local codes: performed | not performed | partially performed
│     │  │  ├─ CLUSTER "Left lateral canal"            [0..1]
│     │  │  │  ├─ ELEMENT "VOR gain"                   DV_QUANTITY    [0..1]  units "1", 0..3, precision 2
│     │  │  │  ├─ ELEMENT "Number of valid impulses"   DV_COUNT       [0..1]  >=0
│     │  │  │  ├─ ELEMENT "Mean peak head velocity"    DV_QUANTITY    [0..1]  "deg/s", 0..1000
│     │  │  │  ├─ ELEMENT "Covert saccades"            DV_CODED_TEXT  [0..1]  present | absent
│     │  │  │  ├─ ELEMENT "Overt saccades"             DV_CODED_TEXT  [0..1]  present | absent
│     │  │  │  ├─ ELEMENT "Mean saccade latency"       DV_QUANTITY    [0..1]  "ms", 0..1000
│     │  │  │  ├─ ELEMENT "Mean saccade peak velocity" DV_QUANTITY    [0..1]  "deg/s", 0..1000
│     │  │  │  ├─ ELEMENT "PR score"                   DV_QUANTITY    [0..1]  units "1", 0..100
│     │  │  │  ├─ ELEMENT "Interpretation"             DV_CODED_TEXT  [0..1]  normal | abnormal | inconclusive
│     │  │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  │  ├─ CLUSTER "Right lateral canal"           [0..1]  (same elements as Left lateral canal)
│     │  │  ├─ ELEMENT "Gain asymmetry"                DV_PROPORTION  [0..1]  percent, 0..100
│     │  │  └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
│     │  ├─ CLUSTER "LARP plane"  [0..1]  (HIMP, left anterior – right posterior plane)
│     │  │  ├─ ELEMENT "Test status"                   DV_CODED_TEXT  [0..1]
│     │  │  ├─ CLUSTER "Left anterior canal"           [0..1]  (same elements as Left lateral canal)
│     │  │  ├─ CLUSTER "Right posterior canal"         [0..1]  (same elements as Left lateral canal)
│     │  │  ├─ ELEMENT "Gain asymmetry"                DV_PROPORTION  [0..1]
│     │  │  └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
│     │  ├─ CLUSTER "RALP plane"  [0..1]  (HIMP, right anterior – left posterior plane)
│     │  │  ├─ ELEMENT "Test status"                   DV_CODED_TEXT  [0..1]
│     │  │  ├─ CLUSTER "Right anterior canal"          [0..1]  (same elements as Left lateral canal)
│     │  │  ├─ CLUSTER "Left posterior canal"          [0..1]  (same elements as Left lateral canal)
│     │  │  ├─ ELEMENT "Gain asymmetry"                DV_PROPORTION  [0..1]
│     │  │  └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
│     │  ├─ CLUSTER "SHIMP"  [0..1]  (suppression head impulse paradigm, horizontal plane)
│     │  │  ├─ ELEMENT "Test status"                   DV_CODED_TEXT  [0..1]
│     │  │  ├─ CLUSTER "Left lateral canal"            [0..1]
│     │  │  │  ├─ ELEMENT "SHIMP gain"                 DV_QUANTITY    [0..1]  units "1", 0..3, precision 2
│     │  │  │  ├─ ELEMENT "Number of valid impulses"   DV_COUNT       [0..1]  >=0
│     │  │  │  ├─ ELEMENT "Mean peak head velocity"    DV_QUANTITY    [0..1]  "deg/s", 0..1000
│     │  │  │  ├─ ELEMENT "Anticompensatory saccades"  DV_CODED_TEXT  [0..1]  present | absent
│     │  │  │  ├─ ELEMENT "Residual covert saccades"   DV_CODED_TEXT  [0..1]  present | absent
│     │  │  │  ├─ ELEMENT "Mean anticompensatory saccade latency"        DV_QUANTITY  [0..1]  "ms"
│     │  │  │  ├─ ELEMENT "Mean anticompensatory saccade peak velocity"  DV_QUANTITY  [0..1]  "deg/s"
│     │  │  │  ├─ ELEMENT "Interpretation"             DV_CODED_TEXT  [0..1]  normal | abnormal | inconclusive
│     │  │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  │  ├─ CLUSTER "Right lateral canal"           [0..1]  (same elements as SHIMP Left lateral canal)
│     │  │  ├─ ELEMENT "Gain asymmetry"                DV_PROPORTION  [0..1]
│     │  │  └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
│     │  ├─ ELEMENT "Overall interpretation"           DV_TEXT        [0..1]
│     │  ├─ ELEMENT "Comment"                          DV_TEXT        [0..1]
│     │  └─ SLOT CLUSTER "Multimedia representation"   [0..*]  openEHR-EHR-CLUSTER.media_file.v1
│     └─ state: ITEM_TREE
│        └─ ELEMENT "Confounding factors"              DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Device"                                 DV_TEXT        [0..1]
   ├─ ELEMENT "Software version"                       DV_TEXT        [0..1]
   ├─ ELEMENT "Recorded eye"                           DV_CODED_TEXT  [0..1]  right eye | left eye | both eyes
   ├─ ELEMENT "Gain calculation method"                DV_CODED_TEXT  [0..1]
   │     local codes: instantaneous gain at 40 ms | at 60 ms | at 80 ms | regression gain |
   │                  area under the curve ratio | other
   ├─ ELEMENT "Target distance"                        DV_QUANTITY    [0..1]  "cm"
   └─ SLOT CLUSTER "Extension"                         [0..*]  any CLUSTER
```

## Dizziness Handicap Inventory (DHI) – `openEHR-EHR-OBSERVATION.dizziness_handicap_inventory.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.dizziness_handicap_inventory.v1   "Dizziness Handicap Inventory (DHI)"
├─ data: HISTORY
│  └─ events: EVENT  (time = when the assessment was done)
│     └─ data: ITEM_TREE
│        ├─ CLUSTER "Physical subscale"  [0..1]
│        │  ├─ ELEMENT "P1: Does looking up increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "P2: Does bending over increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "P3: Does performing quick movements of your head increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "P4: Does getting in or out of bed increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "P5: Does reaching up increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "P6: Does walking down the sidewalk increase your problem?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  └─ ELEMENT "P7: Does walking up or down a hill increase your problem?" DV_ORDINAL     [0..1]
│        │           ordinal: 0=No | 2=Sometimes | 4=Yes
│        ├─ CLUSTER "Emotional subscale"  [0..1]
│        │  ├─ ELEMENT "E1: Because of your problem, do you feel embarrassed in front of others?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E2: Because of your problem, do you feel frustrated?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E3: Because of your problem, are you afraid to leave your home without having someone accompany you?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E4: Has your problem placed stress on your relationships with members of your family or friends?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E5: Because of your problem, are you afraid to be home alone?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E6: Because of your problem, are you depressed?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E7: Does your problem interfere with your job or household responsibilities?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "E8: Because of your problem, do you have difficulty concentrating?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  └─ ELEMENT "E9: Because of your problem, do you find it difficult to walk around your house in the dark?" DV_ORDINAL     [0..1]
│        │           ordinal: 0=No | 2=Sometimes | 4=Yes
│        ├─ CLUSTER "Functional subscale"  [0..1]
│        │  ├─ ELEMENT "F1: Because of your problem, do you have difficulty doing housework or yard work?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F2: Because of your problem, is it difficult for you to get into or out of bed?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F3: Because of your problem, do you have difficulty going to a restaurant, movies, or to a party?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F4: Because of your problem, is it difficult for you to walk on uneven ground?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F5: Because of your problem, do you have difficulty with strenuous activities such as sports or dancing?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F6: Because of your problem, is it difficult for you to go to the movies, or to a party or to a dinner out?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F7: Because of your problem, do you have difficulty reading?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  ├─ ELEMENT "F8: Because of your problem, does performing more ambitious activities like sports, dancing, or household chores such as sweeping or putting dishes away reduce your activities or ambitions?" DV_ORDINAL     [0..1]
│        │  │        ordinal: 0=No | 2=Sometimes | 4=Yes
│        │  └─ ELEMENT "F9: Because of your problem, is it difficult for you to walk?" DV_ORDINAL     [0..1]
│        │           ordinal: 0=No | 2=Sometimes | 4=Yes
│        ├─ ELEMENT "Physical subscale score"       DV_COUNT       [0..1]
│        │        range 0..28
│        ├─ ELEMENT "Emotional subscale score"      DV_COUNT       [0..1]
│        │        range 0..36
│        ├─ ELEMENT "Functional subscale score"     DV_COUNT       [0..1]
│        │        range 0..36
│        ├─ ELEMENT "Total DHI score"               DV_COUNT       [0..1]
│        │        range 0..100
│        ├─ ELEMENT "Handicap severity"             DV_CODED_TEXT  [0..1]
│        │        local codes: No handicap (0–16) | Mild handicap (18–36) | Moderate handicap (38–52) | Severe handicap (54–100)
│        └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Administration method"               DV_CODED_TEXT  [0..1]
   │        local codes: Self-administered | Clinician-administered (interview) | Proxy-reported
   ├─ ELEMENT "Questionnaire language"              DV_TEXT        [0..1]
   ├─ ELEMENT "Version"                             DV_TEXT        [0..1]
   └─ SLOT CLUSTER "Extension"                                     [0..*]  any CLUSTER
```

## Visual Vertigo Analog Scale (VVAS) – `openEHR-EHR-OBSERVATION.visual_vertigo_analog_scale.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.visual_vertigo_analog_scale.v1   "Visual Vertigo Analog Scale (VVAS)"
├─ data: HISTORY
│  └─ events: EVENT  (time = when the assessment was done)
│     ├─ data: ITEM_TREE
│     │  ├─ CLUSTER "Item 1: Walking through a supermarket aisle"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 2: Being a passenger in a car"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 3: Being under fluorescent lights"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 4: Watching traffic at a busy intersection"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 5: Walking through a shopping mall"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 6: Going down an escalator"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 7: Watching a movie at the movie theatre"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 8: Walking over a patterned floor"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ CLUSTER "Item 9: Watching action television"  [0..1]
│     │  │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Performed | Not performed | Partially performed
│     │  │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│     │  │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│     │  │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│     │  ├─ ELEMENT "Total VVAS score"              DV_QUANTITY    [0..1]
│     │  │        property: Qualified real, units "1", range 0..100, precision 1
│     │  ├─ ELEMENT "Number of items completed"     DV_COUNT       [0..1]
│     │  │        range 1..9
│     │  ├─ CLUSTER "Symptom qualifiers"  [0..1]
│     │  │  ├─ ELEMENT "Predominant symptom"        DV_CODED_TEXT  [0..1]
│     │  │  │        local codes: Dizziness | Disorientation | Nausea | Unsteadiness | Other
│     │  │  └─ ELEMENT "Symptom qualifier comment"  DV_TEXT        [0..1]
│     │  └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
│     └─ state: ITEM_TREE
│        └─ ELEMENT "Confounding factors"           DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Administration method"               DV_CODED_TEXT  [0..1]
   │        local codes: Self-administered (paper) | Self-administered (electronic) | Clinician-administered (interview) | Proxy-reported
   ├─ ELEMENT "Scale format"                        DV_CODED_TEXT  [0..1]
   │        local codes: 10 cm visual analog scale (pen and paper) | Numeric rating scale 0–10 (digital)
   ├─ ELEMENT "Questionnaire language"              DV_TEXT        [0..1]
   ├─ ELEMENT "Version"                             DV_TEXT        [0..1]
   └─ SLOT CLUSTER "Extension"                                     [0..*]  any CLUSTER
```

## Visual Motion Sensitivity – `openEHR-EHR-OBSERVATION.visual_motion_sensitivity.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.visual_motion_sensitivity.v1   "Visual Motion Sensitivity"
├─ data: HISTORY
│  └─ events: EVENT  (time = when the assessment was done)
│     └─ data: ITEM_TREE
│        ├─ CLUSTER "Optokinetic - motionless"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optokinetic - movement to the left"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optokinetic - movement to the right"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optokinetic - upward movement"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optokinetic - downward movement"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optical flow - motionless"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optical flow - forward direction"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Optical flow - backward direction"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Application version"                 DV_TEXT        [0..1]
   ├─ ELEMENT "Virtual reality device"              DV_TEXT        [0..1]
   └─ SLOT CLUSTER "Extension"                                     [0..*]  any CLUSTER
```

## CrowdVR assessment – `openEHR-EHR-OBSERVATION.crowd_vr_assessment.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.crowd_vr_assessment.v1   "CrowdVR assessment"
├─ data: HISTORY
│  └─ events: EVENT  (time = when the assessment was done)
│     └─ data: ITEM_TREE
│        ├─ CLUSTER "Shop environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Narrow corridor environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Shopping center ground floor environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Shopping center first floor environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Metro station environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "City intersection environment"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Application version"                 DV_TEXT        [0..1]
   ├─ ELEMENT "Virtual reality device"              DV_TEXT        [0..1]
   └─ SLOT CLUSTER "Extension"                                     [0..*]  any CLUSTER
```

### EscalatorVR assessment – `openEHR-EHR-OBSERVATION.escalator_vr_assessment.v1`

```
OBSERVATION  openEHR-EHR-OBSERVATION.escalator_vr_assessment.v1   "EscalatorVR assessment"
├─ data: HISTORY
│  └─ events: EVENT  (time = when the assessment was done)
│     └─ data: ITEM_TREE
│        ├─ CLUSTER "Observing a moving escalator at low speed"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        ├─ CLUSTER "Observing a moving escalator at high speed"  [0..1]
│        │  ├─ ELEMENT "Assessment status"          DV_CODED_TEXT  [0..1]
│        │  │        local codes: Performed | Not performed | Partially performed
│        │  ├─ ELEMENT "VAS score"                  DV_QUANTITY    [0..1]
│        │  │        property: Qualified real, units "1", range 0..10, precision 0 or 1
│        │  └─ ELEMENT "Comment"                    DV_TEXT        [0..1]
│        └─ ELEMENT "Comment"                       DV_TEXT        [0..1]
└─ protocol: ITEM_TREE
   ├─ ELEMENT "Application version"                 DV_TEXT        [0..1]
   ├─ ELEMENT "Virtual reality device"              DV_TEXT        [0..1]
   └─ SLOT CLUSTER "Extension"                                     [0..*]  any CLUSTER
```
