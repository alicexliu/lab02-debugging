# lab02-debugging
Alice Liu and Rin Fukuoka <br>
Link to Shadertoy: https://www.shadertoy.com/view/wflfDf#

# Bugs Found and Corrected
**BUG 1:** syntax error: changed vec to vec2. Error was highlighted by shadertoy. <br>
vec uv2 = 2.0 * uv - vec2(1.0); -> vec2 uv2 = 2.0 * uv - vec2(1.0);

**BUG 2:** used wrong uv: changed uv to uv2. We noticed that the scene was not centered correctly. <br>
raycast(uv, dir, eye, ref); -> raycast(uv2, dir, eye, ref);

**BUG 3:** divided by the wrong resolution: changed iResolution.x to iResolution.y. We noticed it because the scene look stretched. <br>
H *= len * iResolution.x / iResolution.x; -> H *= len * iResolution.x / iResolution.y;

**BUG 4:** reflected the eye instead of dir. We noticed that there were no reflections. <br>
dir = reflect(eye, nor); -> dir = reflect(dir, nor);

**BUG 5:** increased the number of march interations from 64 to 256. We noticed that the floor was not being rendered all the way up and around the spheres. We narrowed it down to a marching error since that is how intersections are found. <br>
for(int i = 0; i < 64; ++i) -> for(int i = 0; i < 256; ++i) 


# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
