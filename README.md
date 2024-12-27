# forked version for NAIv4 curated preview support
<strong>*Only T2I might work now.*</strong>
### How to use NAIv4 character prompt function
"CHAR:" prefix is equal to "Add Character" boxes at NAI site.<br />
                    Or, you can also use '|' to separate character information.<br />
                    (Seems same to me, but NAI blog says the first way is recommended.)<br />
                    (Note that it is NOT possible to mix the | prompt and the CHAR: prompt.)<br />
                    Max 6 character prompts available(more than 6 will be ignored).<br />
                    Can be used at both positive and negative.<br /><br />
                    *Prompt example*:<br />
                    &emsp;2girls, couple, sitting together, holding hands, looking at another, facing viewer<br />
                    &emsp;CHAR: aoki reika, smile precure!, nanairogaoka middle school uniform<br />
                    &emsp;CHAR: dawn \(pokemon\), pokemon dppt, pink miniskirt, black vest, sleeveless<br /><br />

### How to use manual character positioning
You can use "POS:" prefix under "CHAR:" line, to add character position coordinates.<br />
                    "POS:" prefix is only compatible with "CHAR:" syntax, not "|" syntax.<br />
                    If there is no "POS:" prefix, the character will be placed by "AI's Choice".<br />
                    The coordinates are like below.
                    
<pre><code>0.1,0.1 | 0.3,0.1 | 0.5,0.1 | 0.7,0.1 | 0.9,0.1
 ---------------------------------------------
0.1,0.3 | 0.3,0.3 | 0.5,0.3 | 0.7,0.3 | 0.9,0.3
 ---------------------------------------------
0.1,0.5 | 0.3,0.5 | 0.5,0.5 | 0.7,0.5 | 0.9,0.5
 ---------------------------------------------
0.1,0.7 | 0.3,0.7 | 0.5,0.7 | 0.7,0.7 | 0.9,0.7
 ---------------------------------------------
0.1,0.9 | 0.3,0.9 | 0.5,0.9 | 0.7,0.9 | 0.9,0.9
</code></pre>
</code>

*Prompt example*:<br />
                    &emsp;2girls, sunny outdoors, sunbeam, looking at another, <br />
                    &emsp;CHAR: sabrina \(pokemon\), pokemon hgss, black hair, red eyes<br />
                    &emsp;POS: 0.3,0.5<br />
                    &emsp;CHAR: dawn \(pokemon\), pokemon, blue hair, blue eyes<br />
                    &emsp;POS: 0.9,0.9<br /><br />
                    
### You must use * instead of # for Action Tags feature.
WebUI seems to ignore all prompts after # character, so I made \* to work instead of #.<br />
                    For example, "target#pointing" becomes "target\*pointing" here.<br /><br />
                    *Prompt example*:<br />
                    &emsp;official style, 2girls,<br />
                    &emsp;CHAR: aoki reika, smile precure!, source\*pointing at another, laughing, nanairogaoka middle school uniform, <br />
                    &emsp;CHAR: dawn \(pokemon\), pokemon dppt, target\*pointing, wavy mouth, full-face blush, shy<br /><br />

![image](https://github.com/user-attachments/assets/870f0010-ff13-49df-81f3-8e0acb893a75)





# sdwebui-nai-api - Novel AI Image Gen in stable-diffusion webui

### An an extension for A1111's stable-diffusion-webui that pulls images using NovelAI's Image Generation Tool API.

#### Requires an active Novel AI account with Opus or Anlas to spend (NOT FREE). You will need to generate a NovelAI API Token for your account, and enter it into the NAI API section in sd-webui settings menu. See [https://docs.sillytavern.app/usage/api-connections/novelai] for details on generating an API key.

Install using "Extensions > Install from URL" using the repo's URL.

- Supports Text2Image, Image2Image, and Inpainting using NovelAI's API
- Supports an A1111 style img2img inpainting mode with an adjustable Denoise Strength.
- Supports a number of A1111 scripts/extensions, such as XYZ Grid generation, Wildcards, Adetailer, SD Upscale
- Allows much higher precision Inpainting masks, as well as uploading masks from other sources.
- Allows feeding NAI generations directly into A1111's Local Image2Image, for a sort of multi-model hi-res fix.
- Automatically translates A1111 format weighted prompts to NovelAI's format eg (1girl:1.1) > {{1girl}} (Values can't be 1:1, but should be close enough)
- Includes a modified version of the Stealth PNG Info extension to fully support NovelAI's stealth PNG info, for sites that strip metadata.
- Optionally Enforces Opus' Free generation limits to avoid wasting Anlas
- Always download every generated image, with A1111's custom filename support

Most locally run extension are NOT supported, obviously. Anything that alter's model behavior is a no go. 
It does support basic extensions/Scripts that only modify generation parameters such as wildcards, or intiate generation, such as XYZ Grid, ADetailer, and SD Upscale.
Running this with certain extensions on may break things. 
 
### Note that this is compltely unaffiliated with NovelAI, and I can make no guarantees as to whether this is an allowable usage of Novel AI's services. However, since they provide the means for you to generate an API Token, I believe it is an acceptable use. IE use at you own risk, but you are probably ok if you don't do something stupid like leave generate forever on for days.


#### Unsupported/TODO
- NAI ControlNet Tools - Not sure how CN works in NAI, not worth worrying about until NAIv3 supports 'em
- NAI Batch support - This isn't free in the only NAI offering worth paying for, so I haven't bothered. (A1111 Batches are pulled sequentially)
- Separate Prompts for NAI/Local in Two pass Image2Image mode.
