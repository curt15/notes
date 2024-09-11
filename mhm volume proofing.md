VOLUME PROOFING

simple volume

- The standard formula for calculating volume = sets x reps x wt

- Within a standard “sets x reps” scheme (e.g. 3x10), calculating volume off of the “average weight” performed is equivalent to applying the formula on each weight instance, e.g.:


Bench Press 3x10 135

3 \* 10 \* 135

vol = 4050

……vs……

Bench Press 3x10 125,135,145

(125+135+145)/3
wt_avg = 135.0

3 \* 10 \* 135
vol = 4050

(10\*125) + (10\*135) + (10\*145)
vol = 4050

________________________________

**vol w/ changing reps**

- When the “sets x reps” scheme changes (e.g. 3 sets x 5 -> 3 -> 1 reps) , the same is not true when applying the formula to the average number of the reps performed on the wt_avg. E.g.:

Bench Press 3x10,8,6 160,170,175

3 \* ((10+8+6)/3) \* ((160+170+175)/3)
vol = 4040.0

(10\*160) + (8\*170) + (6\*175)
vol = 4010

……or……

Bench Press 4x5,3,2,1 225,235,245,255

4 \* ((5+3+2+1)/4) \* ((225+235+245+255)/4)
vol = 2640.0

(5\*225) + (3\*235) + (2\*245) + (1\*255)
vol = 2575



	…MORE EXAMPLES…


Back Squat 5x3,2,1,2,1 315,335,345,330,355

5 \* ((3+2+1+2+1)/5) \* ((315+335+345+330+355)/5)
vol = 3024.0

(3\*315) + (2\*335) + (1\*345) + (2\*330) + (1\*355)
vol = 2975

Back Squat 5x8,6,4,6,4 315,335,345,330,355

5 \* ((8+6+4+6+4)/5) \* ((315+335+345+330+355)/5)
vol = 9408.0

(8\*315) + (6\*335) + (4\*345) + (6\*330) + (4\*355)
vol = 9310


Sumo Deadlift 3x5,3,1 425,445,460

3 \* ((5+3+1)/3) \* ((425+445+460)/3)
vol = 3990

(5\*425) + (3\*445) + (1\*460)
vol = 3920

- (Note: this is really just a minor rounding error that could add up to volume over time, but the main difference comes when paying attention to intensity achievements (rep maxes, etc.))

__________________________________

__________________________________

“DOUBLING”

doubling volume vs doubling weight
- When recording weights on dumbbell (and dual kettlebell) exercises, it is more practical to keep track of the number on the bell vs the “total weight moved” (e.g. 60’s vs 120#).

- In practice, simply doubling the volume (“dbl_vol”) rather than each weight achieves the same result:

DB Bench 3x12,10,8 45,50,55

((12\*45) + (10\*50) + (8\*55)) \* 2

vol = 2690

(12\*90) + (10\*100) + (8\*110)

vol = 2960

(note: still not much of a difference between volume calculation techniques…)

(3 \* ((12+10+8)/3) \* ((45+50+55)/3)) \* 2
vol = 3000.0

__________________________________

what about unilateral/alternating exercises (“**ea**”)?

doubling volume vs doubling reps
- Doubling the volume vs doubling each weight instance seems to make even more “practical” sense when looking at DB/Dual KB unilateral movements (in terms of intensity):
- e.g.: Alt DB Bench 3x10ea @ 60#  != Alt DB Bench 3x10ea 120# (“Single Arm Dumbbell Bench”)
- though… Alt DB Bench 3x10ea @ 60#  ==  DB Bench 3x10 @ 120#  (in terms of total volume)
- e.g.: DB Rows 3x10ea 60#  !=  DB Rows 3x10ea 120#  (“Lawnmover Rows”)
- though… DB Rows 3x10ea 60#  ==  DB BO Row 3x10 120#  (“Dumbbell Bent Over Row”)

 
…so then the reps should be doubled?

DB Rows @ 3 sets x 20 reps x 60 lbs = 3600
DB BO Rows @ 3 sets x 10 reps x 120 lbs = 3600
- for both exercises each arm experiences 60 lbs of intensity, 10 times.

- “unilateral volume” is the same.

Alt DB Bench 3x12,10,8 (ea) 45,50,55

((12\*45) + (10\*50) + (8\*55)) \* 2
vol = 2690

(24\*45) + (20\*50) + (16\*55)
vol = 2960

- dbl_vol vs doubling reps is, again, effectively the same; and both seem legit.

__________________________________

but which is the best option?
and is it best for all DB/KB movements? 


**… (OVER)THOUGHT EXPERIMENT …**

Dual KB Front Squat 3x10 25kg (55 lbs ea bell = 110 lbs total)
					V.S.
DB Split Squats 3x10ea 25kg (same 55 lb bells in each hand = 110 lbs)

Possibilities:
vol calc  =  standard (simp_vol) OR “double volume” (dbl_vol)
reps       =  as recorded OR doubled (“unilateral volume” rule)
wts         =  as recorded OR doubled (“total weight moved” rule)

vol_calc      reps        wts           CALCULATION                  VOL
1 - simp_vol    reps         wts          >>> 3 * 10 * 55                   1650 
2 - simp_vol    reps x2    wts          >>> 3 * 20 * 55                   3300
3 - simp_vol    reps         wts x2     >>> 3 * 10 * 110                 3300
4 - simp_vol    reps x2    wts x2     >>> 3 * 20 * 110                 660                                                    
**5 - dbl_vol      reps        wts        >>> (3 * 10 * 55) * 2            3300**
6 - dbl_vol       reps x2    wts         >>> (3 * 20 * 55) * 2            6600
7 - dbl_vol       reps         wts x2    >>> (3 * 10 * 110) * 2          6600 
8 - dbl_vol       reps x2    wts x2    >>> (3 * 20 * 110) * 2          13200


--- 


Breakdown:

Dual KB Front Squat = “FS”
DB Split Squats = “SS”

\# NO!: (vol=WRONG)
\1. totally inaccurate for either — volume isn’t accounting for the actual weight held anywhere…
\8. inaccurate for either (especially FS volume) — volume already accounts for “unilateral volume” via reps x2 and “total weight moved” via wts x2; shouldn’t be doubled again…


\# MEH…: (vol=6600)
6. inaccurate representation of SS unilateral intensity (& totally inaccurate FS volume)
4. SS? — but, …? (& totally inaccurate FS volume)
7. OK for SS —  inaccurate representation of SS unilateral volume (& inappropriate FS dbl_vol)


\# MEH…: (vol=3300)
3. Good for FS — but, inaccurate representation of SS unilateral volume
2. bad for SS — inaccurate representation of unilateral intensity (& totally inaccurate FS volume)

**5. This is the current strategy being deployed on both cases — is this correct? (vol=3300)**


whittling down options…

FS — 3,5 (best=3,  vol=3300)

3 = obvious choice in accurate FS representation



SS —

4,7,6 (best_of=4, vol=6600)
4 =  “3 \* 20 \* 110” (inaccurate total vol?)
7 =  “(3 \* 10 \* 110) \* 2” (inaccurate total reps?)

OR

3,5 (best_of=??, vol=3300)
3 =  “3 * 10 * 110”  (inaccurate single leg volume?)
5 =  “(3 * 10 * 55) * 2” (inaccurate single leg intensity?)

so the question becomes what then??
Are Front Squat and Split Squat sets done with the same “total reps” proportional… 
- in single leg intensity?
	NO - 
	… each leg in this theoretical Split Squat experiences 110# for “each rep”
	… each leg in this theoretical Front Squat experiences 55# for “each rep”
- in total volume?
	… each leg experiences 10 total reps in both theoretical FS & SS

“EUREKA!”

************************

** Dual KB Front Squat = 3 sets x 10 reps x 110lbs = 3300 ** 

DB Split Squats = 3 sets x 20 reps x 110 lbs = 6600

DB Split Squats = (3 sets x 10 reps x 110 lbs) x2 legs = 6600


** DB BO Row = 3 sets x 10 reps x 110 lbs = 3300 ** 

DB Rows = 3 sets x 20 reps x 55 lbs = 3300

DB Rows = (3 sets x 10 reps x 55 lbs) x2 arms = 3300



** DB Bench = 3 sets x 10 reps x 110lbs = 3300 **

Alt DB Bench = 3 sets x 20 reps x 55lbs = 3300

Alt DB Bench = (3 sets x 10 reps x 55lbs) x2 arms = 3300

************************
In the case of a “Dual KB Front Squat” vs “DB Split Squats”:
- Front Squat - weight is appropriately doubled
- Split Squats - weight is appropriately doubled, AND volume is appropriately doubled

In the case of a “DB BO Row” vs “DB Rows (ea)”:
- DB BO Row - weight is appropriately doubled
- DB Rows - volume is appropriately doubled
(note: applicable to above DB Bench Press vars)

________________________________________

CONCLUSION

Although doubling reps vs doubling volume (vs doubling weight… or any combination of “doubling”) are obviously functionally the same and don’t make a difference at all in the result of a volume calculation (sets x reps x weight) ala order of operations, this over-though experiment has helped me make sure I know when to apply which and why.

Even though choosing to apply double reps vs volume to all of the above “single limb vars” both seem like accurate representations of the set, I will probably maintain the rep count and keep the dbl_vol approach in this project — sticking to meathead mathematical semantics, where a set of 3-5 vs 10-12 vs 20 holds certain assumptions in terms of things like intensity or neuromuscular outcomes.

Even though in the DB Row/Bench variations, it might seem to make more “practical” sense to choose double weight in “bilat” and dbl_vol in “unilat” vars, when breaking down all movement examples used:

DB Bench 3x10 55 = 3 sets x 10 reps x 110 lbs = 3300
                        = *** (3 sets x 10 reps x 55 lbs) x2 arms ***

Alt DB Bench 3x10ea 55 = 3 sets x 20 reps x 55 lbs = 3300
                        = (3 sets x 10 reps x 55 lbs) x2 arms

DB BO Rows 3x10 55 = 3 sets x 10 reps x 110 lbs = 3300
                        = *** (3 sets x 10 reps x 55 lbs) x2 arms ***

DB Rows 3x10ea 55 = 3 sets x 20 reps x 55 lbs = 3300
                        = (3 sets x 10 reps x 55 lbs) x2 arms

Dual KB Front Squat 3x10 55 = *** 3 sets x 10 reps x 110 lbs = 3300 ***

DB Split Squats 3x10ea 55 = 3 sets x 20 reps x 110 lbs = 6600
                                            = (3 sets x 10 reps x 110 lbs) x2 legs

the total weight moved in the “DB Bench/BO Row” and “Dual KB Front Squat” is indeed 110#, but in choosing (“** **”) to represent volume differently in the individual cases, meathead syntax is better reserved — where Squat vars are all typically understood in terms of total weight moved, but the standard nomenclature for Press/Pull vars makes for a different understanding:

(Front Squat @ 110#  ==  Dual KB Front Squat @ 110#  ==  Goblet Squat @ 110#)

(Bench Press @ 110#  !=  DB Bench @ 110#)

(BO Row @ 110#  !=  Lawnmower Row @ 110#)

_______________

**APPLICATION TO EDGE CASES & “BODYBUILDING” EXERCISES**:

Core Bodybuilding Exercises = Curls, Tricep Ext, Fly, Shoulder Raises,

modalities = DB, Cable, MAC, BB

- With each modality applied to “Curls” and “Tricep Extensions”, the rules remain the same as above: (DB Curls @ 30#  ==  BB Curls @ 60#  ==  Cable Curls @ 60#  ==  MAC Curls @ 60#)

- No special case changes are needed to BB, Cable, & MAC vars — the single weight stack moved accounts for the total weight and volume remains equivalent.

- When the Cable modality is applied to “Chest Fly” and “Shoulder Raises”, the total weight is split between two separate weight stacks. In these cases, the modalities should follow the same rule for DB Pressing/Pulling —  with volume doubled.
(DB Fly @ 30#  ==  Cable Fly @ 30#)

- When the MAC modality is applied to “Chest Fly”, the total weight on the stack applies to both limbs. To keep volume rules and intensity tracking uniform to the DB & Cable modailties in this specific case — I’m using weights/2, with volume doubled.
(DB Fly @ 50#  ~=  MAC Fly @ 100#)