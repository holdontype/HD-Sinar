## FontBakery report

fontbakery version: 0.13.1





## Experimental checks

These won't break the CI job for now, but will become effective after some time if nobody raises any concern.


<details><summary>[1] Sinar-ReversedVF.ttf</summary>
<div>
<details>
    <summary>✅ <b>PASS</b> Check base characters have non-zero advance width. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#base-has-width">base_has_width</a></summary>
    <div>


> 
> Base characters should have non-zero advance width.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4906





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>
</div>
</details>




## All other checks



<details><summary>[114] Sinar-ReversedVF.ttf</summary>
<div>
<details>
    <summary>🔥 <b>FAIL</b> Axes and named instances fall within correct ranges? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-fvar-regular-coords-correct">opentype/fvar/regular_coords_correct</a></summary>
    <div>


> 
> According to the Open-Type spec's registered design-variation tags,instances in a variable font should have certain prescribed values.
> If a variable font has a 'wght' (Weight) axis, the valid coordinate range is 1-1000.
> If a variable font has a 'wdth' (Width) axis, the valid numeric range is strictly greater than zero.
> If a variable font has a 'slnt' (Slant) axis, then the coordinate of its 'Regular' instance is required to be 0.
> If a variable font has a 'ital' (Slant) axis, then the coordinate of its 'Regular' instance is required to be 0.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1707
> See also: https://github.com/fonttools/fontbakery/issues/2572





* 🔥 **FAIL** <p>&quot;Regular&quot; instance not present.</p>
 [code: no-regular-instance]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Ensure the font supports case swapping for all its glyphs. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#case-mapping">case_mapping</a></summary>
    <div>


> 
> Ensure that no glyph lacks its corresponding upper or lower counterpart
> (but only when unicode supports case-mapping).
> 




> Original proposal: https://github.com/googlefonts/fontbakery/issues/3230





* 🔥 **FAIL** <p>The following glyphs lack their case-swapping counterparts:</p>
<table>
<thead>
<tr>
<th align="left">Glyph present in the font</th>
<th align="left">Missing case-swapping counterpart</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">U+0166: LATIN CAPITAL LETTER T WITH STROKE</td>
<td align="left">U+0167: LATIN SMALL LETTER T WITH STROKE</td>
</tr>
<tr>
<td align="left">U+01C4: LATIN CAPITAL LETTER DZ WITH CARON</td>
<td align="left">U+01C6: LATIN SMALL LETTER DZ WITH CARON</td>
</tr>
<tr>
<td align="left">U+01F1: LATIN CAPITAL LETTER DZ</td>
<td align="left">U+01F3: LATIN SMALL LETTER DZ</td>
</tr>
<tr>
<td align="left">U+1E0C: LATIN CAPITAL LETTER D WITH DOT BELOW</td>
<td align="left">U+1E0D: LATIN SMALL LETTER D WITH DOT BELOW</td>
</tr>
<tr>
<td align="left">U+1E46: LATIN CAPITAL LETTER N WITH DOT BELOW</td>
<td align="left">U+1E47: LATIN SMALL LETTER N WITH DOT BELOW</td>
</tr>
<tr>
<td align="left">U+1E5A: LATIN CAPITAL LETTER R WITH DOT BELOW</td>
<td align="left">U+1E5B: LATIN SMALL LETTER R WITH DOT BELOW</td>
</tr>
<tr>
<td align="left">U+1E6C: LATIN CAPITAL LETTER T WITH DOT BELOW</td>
<td align="left">U+1E6D: LATIN SMALL LETTER T WITH DOT BELOW</td>
</tr>
</tbody>
</table>
 [code: missing-case-counterparts]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Letters in font have glyphs that are not empty? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#empty-letters">empty_letters</a></summary>
    <div>


> 
> Font language, script, and character set tagging approaches typically have an
> underlying assumption that letters (i.e. characters with Unicode general
> category 'Ll', 'Lm', 'Lo', 'Lt', or 'Lu', which includes CJK ideographs and
> Hangul syllables) with entries in the 'cmap' table have glyphs with ink (with
> a few exceptions, notably the four Hangul "filler" characters: U+115F, U+1160,
> U+3164, U+FFA0).
> 
> This check is intended to identify fonts in which such letters have been mapped
> to empty glyphs (typically done as a form of subsetting). Letters with empty
> glyphs should have their entries removed from the 'cmap' table, even if the
> empty glyphs are left in place (e.g. for CID consistency).
> 
> The check will yield only a WARN if the blank glyph maps to a character in the
> range of Korean hangul syllable code-points, which are known to be used by font
> designers as a workaround to undesired behavior from InDesign's Korean IME
> (Input Method Editor).
> 
> More details available at https://github.com/fonttools/fontbakery/issues/2894
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2460





* 🔥 **FAIL** <p>U+02BB should be visible, but its glyph ('uni02BB') is empty.</p>
 [code: empty-letter]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Checking OS/2 usWinAscent & usWinDescent. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#family-win-ascent-and-descent">family/win_ascent_and_descent</a></summary>
    <div>


> 
> A font's winAscent and winDescent values should be greater than or equal to
> the head table's yMax, abs(yMin) values. If they are less than these values,
> clipping can occur on Windows platforms
> (https://github.com/RedHatBrand/Overpass/issues/33).
> 
> If the font includes tall/deep writing systems such as Arabic or Devanagari,
> the winAscent and winDescent can be greater than the yMax and absolute yMin
> values to accommodate vowel marks.
> 
> When the 'win' Metrics are significantly greater than the UPM, the linespacing
> can appear too loose. To counteract this, enabling the OS/2 fsSelection
> bit 7 (Use_Typo_Metrics), will force Windows to use the OS/2 'typo' values
> instead. This means the font developer can control the linespacing with
> the 'typo' values, whilst avoiding clipping by setting the 'win' values to
> values greater than the yMax and absolute yMin.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* 🔥 **FAIL** <p>OS/2.usWinAscent value should be equal or greater than 1126, but got 1010 instead</p>
 [code: ascent]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Checking if STAT entries matches fvar and vice versa. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#inconsistencies-between-fvar-STAT">inconsistencies_between_fvar_STAT</a></summary>
    <div>


> 
> Check for inconsistencies in names and values between the fvar instances
> and STAT table. Inconsistencies may cause issues in apps like Adobe InDesign.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3636





* 🔥 **FAIL** <p>Reversed Thin: 'wght' axis value '100.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Extralight: 'wght' axis value '200.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Light: 'wght' axis value '300.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed: 'wght' axis value '400.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Medium: 'wght' axis value '500.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Semibold: 'wght' axis value '600.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Bold: 'wght' axis value '700.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Extrabold: 'wght' axis value '800.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



* 🔥 **FAIL** <p>Reversed Heavy: 'wght' axis value '900.0' missing in STAT table.</p>
 [code: missing-fvar-instance-axis-value]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Font contains '.notdef' as its first glyph? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#mandatory-glyphs">mandatory_glyphs</a></summary>
    <div>


> 
> The OpenType specification v1.8.2 recommends that the first glyph is the
> '.notdef' glyph without a codepoint assigned and with a drawing:
> 
> The .notdef glyph is very important for providing the user feedback
> that a glyph is not found in the font. This glyph should not be left
> without an outline as the user will only see what looks like a space
> if a glyph is missing and not be aware of the active font’s limitation.
> 
> https://docs.microsoft.com/en-us/typography/opentype/spec/recom#glyph-0-the-notdef-glyph
> 
> Pre-v1.8, it was recommended that fonts should also contain 'space', 'CR'
> and '.null' glyphs. This might have been relevant for MacOS 9 applications.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* 🔥 **FAIL** <p>The '.notdef' glyph should contain a drawing, but it is blank.</p>
 [code: notdef-is-blank]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Ensure smart dropout control is enabled in "prep" table instructions. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#smart-dropout">smart_dropout</a></summary>
    <div>


> 
> This setup is meant to ensure consistent rendering quality for fonts across
> all devices (with different rendering/hinting capabilities).
> 
> Below is the snippet of instructions we expect to see in the fonts:
> B8 01 FF    PUSHW 0x01FF
> 85          SCANCTRL (unconditinally turn on
> dropout control mode)
> B0 04       PUSHB 0x04
> 8D          SCANTYPE (enable smart dropout control)
> 
> "Smart dropout control" means activating rules 1, 2 and 5:
> Rule 1: If a pixel's center falls within the glyph outline,
> that pixel is turned on.
> Rule 2: If a contour falls exactly on a pixel's center,
> that pixel is turned on.
> Rule 5: If a scan line between two adjacent pixel centers
> (either vertical or horizontal) is intersected
> by both an on-Transition contour and an off-Transition
> contour and neither of the pixels was already turned on
> by rules 1 and 2, turn on the pixel which is closer to
> the midpoint between the on-Transition contour and
> off-Transition contour. This is "Smart" dropout control.
> 
> For more detailed info (such as other rules not enabled in this snippet),
> please refer to the TrueType Instruction Set documentation.
> 
> Generally this occurs with unhinted fonts; if you are not using autohinting,
> use gftools-fix-nonhinting (or just gftools-fix-font) to fix this issue.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* 🔥 **FAIL** <p>The 'prep' table does not contain TrueType instructions enabling smart dropout control. To fix, export the font with autohinting enabled, or run ttfautohint on the font, or run the <code>gftools fix-nonhinting</code> script.</p>
 [code: lacks-smart-dropout]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> Ensure component transforms do not perform scaling or rotation. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#transformed-components">transformed_components</a></summary>
    <div>


> 
> Some families have glyphs which have been constructed by using
> transformed components e.g the 'u' being constructed from a flipped 'n'.
> 
> From a designers point of view, this sounds like a win (less work).
> However, such approaches can lead to rasterization issues, such as
> having the 'u' not sitting on the baseline at certain sizes after
> running the font through ttfautohint.
> 
> Other issues are outlines that end up reversed when only one dimension
> is flipped while the other isn't.
> 
> As of July 2019, Marc Foley observed that ttfautohint assigns cvt values
> to transformed glyphs as if they are not transformed and the result is
> they render very badly, and that vttLib does not support flipped components.
> 
> When building the font with fontmake, the problem can be fixed by adding
> this to the command line:
> 
> --filter DecomposeTransformedComponentsFilter
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2011





* 🔥 **FAIL** <p>The following glyphs had components with scaling or rotation
or inverted outline direction:</p>
<ul>
<li>uni27E9 (component uni27E8)</li>
<li>exclamdown (component exclam)</li>
<li>exclamdown.case (component exclam)</li>
<li>parenright (component parenleft)</li>
<li>braceright (component braceleft)</li>
<li>bracketright (component bracketleft)</li>
<li>parenright.case (component parenleft.case)</li>
<li>braceright.case (component braceleft.case)</li>
<li>bracketright.case (component bracketleft.case)</li>
<li>uni2199 (component uni2198)</li>
<li>arrowleft (component arrowright)</li>
<li>uni2196 (component uni2197)</li>
<li>uni21A6 (component uni21A4)</li>
<li>uni21A7 (component uni21A5)</li>
<li>uni21B1 (component uni21B0)</li>
<li>uni21B2 (component uni21B0)</li>
<li>uni25C1 (component uni25B7)</li>
<li>uni25BF (component uni25B5)</li>
<li>uni25C3 (component uni25B9)</li>
</ul>
 [code: transformed-components]



</div>
</details>

<details>
    <summary>🔥 <b>FAIL</b> The variable font 'wght' (Weight) axis coordinate must be 700 on the 'Bold' instance. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-bold-wght-coord">varfont/bold_wght_coord</a></summary>
    <div>


> 
> The OpenType spec's registered
> design-variation tag 'wght' available at
> https://docs.microsoft.com/en-gb/typography/opentype/spec/dvaraxistag_wght
> does not specify a required value for the 'Bold' instance of a variable font.
> 
> But Dave Crossland suggested that a required value of 700 should be enforced
> in this case (NOTE: a distinction is made between "no bold instance present"
> vs "bold instance is present but its wght coordinate is not == 700").
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1707





* 🔥 **FAIL** <p>&quot;Bold&quot; instance not present.</p>
 [code: no-bold-instance]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Check accent of Lcaron, dcaron, lcaron, tcaron <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#alt-caron">alt_caron</a></summary>
    <div>


> 
> Lcaron, dcaron, lcaron, tcaron should NOT be composed with quoteright
> or quotesingle or comma or caron(comb). It should be composed with a
> distinctive glyph which doesn't look like an apostrophe.
> 
> Source:
> https://ilovetypography.com/2009/01/24/on-diacritics/
> http://diacritics.typo.cz/index.php?id=5
> https://www.typotheque.com/articles/lcaron
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3308





* ✅ **PASS** <p>Looks good!</p>
 



* ⚠️ **WARN** <p>tcaron is decomposed and therefore could not be checked. Please check manually.</p>
 [code: decomposed-outline]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Detect any interpolation issues in the font. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#interpolation-issues">interpolation_issues</a></summary>
    <div>


> 
> When creating a variable font, the designer must make sure that corresponding
> paths have the same start points across masters, as well as that corresponding
> component shapes are placed in the same order within a glyph across masters.
> If this is not done, the glyph will not interpolate correctly.
> 
> Here we check for the presence of potential interpolation errors using the
> fontTools.varLib.interpolatable module.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3930





* ⚠️ **WARN** <p>Interpolation issues were found in the font:</p>
<pre><code>- Contour 0 start point differs in glyph 'fraction' between location wght=400 and location wght=100

- Contour 0 start point differs in glyph 'fraction' between location wght=100 and location wght=900

- Contour 6 start point differs in glyph 'perthousand' between location wght=400 and location wght=100

- Contour 6 start point differs in glyph 'perthousand' between location wght=100 and location wght=900

- Contour 4 start point differs in glyph 'percent' between location wght=400 and location wght=100

- Contour 4 start point differs in glyph 'percent' between location wght=100 and location wght=900
</code></pre>
 [code: interpolation-issues]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Are there caret positions declared for every ligature? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#ligature-carets">ligature_carets</a></summary>
    <div>


> 
> All ligatures in a font must have corresponding caret (text cursor) positions
> defined in the GDEF table, otherwhise, users may experience issues with
> caret rendering.
> 
> If using GlyphsApp or UFOs, ligature carets can be defined as anchors with
> names starting with `caret_`. These can be compiled with fontmake as of
> version v2.4.0.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1225





* ⚠️ **WARN** <p>This font lacks caret positioning values for these ligature glyphs:
- fl</p>
 [code: incomplete-caret-pos-data]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Ensure variable fonts include an avar table. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#mandatory-avar-table">mandatory_avar_table</a></summary>
    <div>


> 
> Most variable fonts should include an avar table to correctly define
> axes progression rates.
> 
> For example, a weight axis from 0% to 100% doesn't map directly to 100 to 1000,
> because a 10% progression from 0% may be too much to define the 200,
> while 90% may be too little to define the 900.
> 
> If the progression rates of axes is linear, this check can be ignored.
> Fontmake will also skip adding an avar table if the progression rates
> are linear. However, it is still recommended that designers visually proof
> each instance is at the expected weight, width etc.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3100





* ⚠️ **WARN** <p>This variable font does not have an avar table. Most variable fonts should include an avar table to correctly define axes progression rates.</p>
 [code: missing-avar]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Check math signs have the same width. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#math-signs-width">math_signs_width</a></summary>
    <div>


> 
> It is a common practice to have math signs sharing the same width
> (preferably the same width as tabular figures accross the entire font family).
> 
> This probably comes from the will to avoid additional tabular math signs
> knowing that their design can easily share the same width.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3832





* ⚠️ **WARN** <p>The most common width is 472 among a set of 9 math glyphs.
The following math glyphs have a different width, though:</p>
<p>Width = 499:
greaterequal, greater, less</p>
<p>Width = 498:
lessequal</p>
 [code: width-outliers]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Does the font contain a soft hyphen? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#soft-hyphen">soft_hyphen</a></summary>
    <div>


> 
> The 'Soft Hyphen' character (codepoint 0x00AD) is used to mark
> a hyphenation possibility within a word in the absence of or
> overriding dictionary hyphenation.
> 
> It is sometimes designed empty with no width (such as a control character),
> sometimes the same as the traditional hyphen, sometimes double encoded with
> the hyphen.
> 
> That being said, it is recommended to not include it in the font at all,
> because discretionary hyphenation should be handled at the level of the
> shaping engine, not the font. Also, even if present, the software would
> not display that character.
> 
> More discussion at:
> https://typedrawers.com/discussion/2046/special-dash-things-softhyphen-horizontalbar
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4046
> See also: https://github.com/fonttools/fontbakery/issues/3486





* ⚠️ **WARN** <p>This font has a 'Soft Hyphen' character.</p>
 [code: softhyphen]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Ensure Stylistic Sets have description. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#stylisticset-description">stylisticset_description</a></summary>
    <div>


> 
> Stylistic sets should provide description text. Programs such as InDesign,
> TextEdit and Inkscape use that info to display to the users so that they know
> what a given stylistic set offers.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3155





* ⚠️ **WARN** <p>The stylistic set ss02 lacks a description string on the 'name' table.</p>
 [code: missing-description]



</div>
</details>

<details>
    <summary>⚠️ <b>WARN</b> Check font contains no unreachable glyphs <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#unreachable-glyphs">unreachable_glyphs</a></summary>
    <div>


> 
> Glyphs are either accessible directly through Unicode codepoints or through
> substitution rules.
> 
> In Color Fonts, glyphs are also referenced by the COLR table. And mathematical
> fonts also reference glyphs via the MATH table.
> 
> Any glyphs not accessible by these means are redundant and serve only
> to increase the font's file size.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3160





* ⚠️ **WARN** <p>The following glyphs could not be reached by codepoint or substitution rules:</p>
<pre><code>- uni0306.cy
</code></pre>
 [code: unreachable-glyphs]



</div>
</details>

<details>
    <summary>ℹ️ <b>INFO</b> List all superfamily filepaths <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#superfamily-list">superfamily/list</a></summary>
    <div>


> 
> This is a merely informative check that lists all sibling families
> detected by fontbakery.
> 
> Only the fontfiles in these directories will be considered in
> superfamily-level checks.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1487





* ℹ️ **INFO** <p>fonts/variable</p>
 [code: family-path]



</div>
</details>

<details>
    <summary>ℹ️ <b>INFO</b> Show hinting filesize impact. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#hinting-impact">hinting_impact</a></summary>
    <div>


> 
> This check is merely informative, displaying an useful comparison of filesizes
> of hinted versus unhinted font files.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ℹ️ **INFO** <p>Hinting filesize impact:</p>
<table>
<thead>
<tr>
<th align="left"></th>
<th align="right">fonts/variable/Sinar-ReversedVF.ttf</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">Dehinted Size</td>
<td align="right">233.0kb</td>
</tr>
<tr>
<td align="left">Hinted Size</td>
<td align="right">233.0kb</td>
</tr>
<tr>
<td align="left">Increase</td>
<td align="right">-24 bytes</td>
</tr>
<tr>
<td align="left">Change</td>
<td align="right">-0.0 %</td>
</tr>
</tbody>
</table>
 [code: size-impact]



</div>
</details>

<details>
    <summary>ℹ️ <b>INFO</b> Font contains all required tables? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#required-tables">required_tables</a></summary>
    <div>


> 
> According to the OpenType spec
> https://docs.microsoft.com/en-us/typography/opentype/spec/otff#required-tables
> 
> Whether TrueType or CFF outlines are used in an OpenType font, the following
> tables are required for the font to function correctly:
> 
> - cmap (Character to glyph mapping)
> - head (Font header)
> - hhea (Horizontal header)
> - hmtx (Horizontal metrics)
> - maxp (Maximum profile)
> - name (Naming table)
> - OS/2 (OS/2 and Windows specific metrics)
> - post (PostScript information)
> 
> The spec also documents that variable fonts require the following table:
> 
> - STAT (Style attributes)
> 
> Depending on the typeface and coverage of a font, certain tables are
> recommended for optimum quality.
> 
> For example:
> - the performance of a non-linear font is improved if the VDMX, LTSH,
> and hdmx tables are present.
> - Non-monospaced Latin fonts should have a kern table.
> - A gasp table is necessary if a designer wants to influence the sizes
> at which grayscaling is used under Windows. Etc.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ℹ️ **INFO** <p>This font contains the following optional tables:</p>
<pre><code>- loca

- GPOS

- GSUB

- vhea

- vmtx
</code></pre>
 [code: optional-tables]



* ✅ **PASS** <p>Font contains all required tables.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check hhea.caretSlopeRise and hhea.caretSlopeRun <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-caret-slope">opentype/caret_slope</a></summary>
    <div>


> 
> Checks whether hhea.caretSlopeRise and hhea.caretSlopeRun
> match with post.italicAngle.
> 
> For Upright fonts, you can set hhea.caretSlopeRise to 1
> and hhea.caretSlopeRun to 0.
> 
> For Italic fonts, you can set hhea.caretSlopeRise to head.unitsPerEm
> and calculate hhea.caretSlopeRun like this:
> round(math.tan(
> math.radians(-1 * font["post"].italicAngle)) * font["head"].unitsPerEm)
> 
> This check allows for a 0.1° rounding difference between the Italic angle
> as calculated by the caret slope and post.italicAngle
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3670





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check code page character ranges <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-code-pages">opentype/code_pages</a></summary>
    <div>


> 
> At least some programs (such as Word and Sublime Text) under Windows 7
> do not recognize fonts unless code page bits are properly set on the
> ulCodePageRange1 (and/or ulCodePageRange2) fields of the OS/2 table.
> 
> More specifically, the fonts are selectable in the font menu, but whichever
> Windows API these applications use considers them unsuitable for any
> character set, so anything set in these fonts is rendered with Arial as a
> fallback font.
> 
> This check currently does not identify which code pages should be set.
> Auto-detecting coverage is not trivial since the OpenType specification
> leaves the interpretation of whether a given code page is "functional"
> or not open to the font developer to decide.
> 
> So here we simply detect as a FAIL when a given font has no code page
> declared at all.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2474





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Font follows the family naming recommendations? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-naming-recommendations">opentype/family_naming_recommendations</a></summary>
    <div>


> 
> This check ensures that the length of various family name and style
> name strings in the name table are within the maximum length
> recommended by the OpenType specification.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking font version fields (head and name table). <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-font-version">opentype/font_version</a></summary>
    <div>


> 
> The OpenType specification provides for two fields which contain
> the version number of the font: fontRevision in the head table,
> and nameID 5 in the name table. If these fields do not match,
> different applications will report different version numbers for
> the font.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking OS/2 fsSelection value. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-fsselection">opentype/fsselection</a></summary>
    <div>


> 
> The OS/2.fsSelection field is a bit field used to specify the stylistic
> qualities of the font - in particular, it specifies to some operating
> systems whether the font is italic (bit 0), bold (bit 5) or regular
> (bit 6).
> 
> This check verifies that the fsSelection field is set correctly for the
> font style. For a family of static fonts created in GlyphsApp, this is
> set by using the style linking checkboxes in the exports settings.
> 
> Additionally, the bold and italic bits in OS/2.fsSelection must match the
> bold and italic bits in head.macStyle per the OpenType spec.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829
> See also: https://github.com/fonttools/fontbakery/pull/2382





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Axes and named instances fall within correct ranges? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-fvar-axis-ranges-correct">opentype/fvar/axis_ranges_correct</a></summary>
    <div>


> 
> According to the OpenType spec's registered design-variation tags, instances in
> a variable font should have certain prescribed values.
> If a variable font has a 'wght' (Weight) axis, the valid coordinate range is 1-1000.
> If a variable font has a 'wdth' (Width) axis, the valid numeric range is strictly greater than zero.
> If a variable font has a 'slnt' (Slant) axis, then the coordinate of its 'Regular' instance is required to be 0.
> If a variable font has a 'ital' (Slant) axis, then the coordinate of its 'Regular' instance is required to be 0.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2264
> See also: https://github.com/fonttools/fontbakery/pull/2520
> See also: https://github.com/fonttools/fontbakery/issues/2572





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check mark characters are in GDEF mark glyph class. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-gdef-mark-chars">opentype/gdef_mark_chars</a></summary>
    <div>


> 
> Mark characters should be in the GDEF mark glyph class.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2877





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check GDEF mark glyph class doesn't have characters that are not marks. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-gdef-non-mark-chars">opentype/gdef_non_mark_chars</a></summary>
    <div>


> 
> Glyphs in the GDEF mark glyph class become non-spacing and may be repositioned
> if they have mark anchors.
> 
> Only combining mark glyphs should be in that class. Any non-mark glyph
> must not be in that class, in particular spacing glyphs.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2877





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check glyphs in mark glyph class are non-spacing. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-gdef-spacing-marks">opentype/gdef_spacing_marks</a></summary>
    <div>


> 
> Glyphs in the GDEF mark glyph class should be non-spacing.
> 
> Spacing glyphs in the GDEF mark glyph class may have incorrect anchor
> positioning that was only intended for building composite glyphs during design.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2877





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check glyphs do not have duplicate components which have the same x,y coordinates. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-glyf-non-transformed-duplicate-components">opentype/glyf_non_transformed_duplicate_components</a></summary>
    <div>


> 
> There have been cases in which fonts had faulty double quote marks, with each
> of them containing two single quote marks as components with the same
> x, y coordinates which makes them visually look like single quote marks.
> 
> This check ensures that glyphs do not contain duplicate components
> which have the same x,y coordinates.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2709





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Is there any unused data at the end of the glyf table? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-glyf-unused-data">opentype/glyf_unused_data</a></summary>
    <div>


> 
> This check validates the structural integrity of the glyf table,
> by checking that all glyphs referenced in the loca table are
> actually present in the glyf table and that there is no unused
> data at the end of the glyf table. A failure here indicates a
> problem with the font compiler.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>There is no unused data at the end of the glyf table.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking post.italicAngle value. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-italic-angle">opentype/italic_angle</a></summary>
    <div>


> 
> The 'post' table italicAngle property should be a reasonable amount, likely
> not more than 30°. Note that in the OpenType specification, the value is
> negative for a rightward lean.
> 
> https://docs.microsoft.com/en-us/typography/opentype/spec/post
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Value of post.italicAngle is 0.0 with style=&quot;Regular&quot;.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Is there a usable "kern" table declared in the font? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-kern-table">opentype/kern_table</a></summary>
    <div>


> 
> Even though all fonts should have their kerning implemented in the GPOS table,
> there may be kerning info at the kern table as well.
> 
> Some applications such as MS PowerPoint require kerning info on the kern table.
> More specifically, they require a format 0 kern subtable from a kern table
> version 0 with only glyphs defined in the cmap table, which is the only one
> that Windows understands (and which is also the simplest and more limited
> of all the kern subtables).
> 
> Google Fonts ingests fonts made for download and use on desktops, and does
> all web font optimizations in the serving pipeline (using libre libraries
> that anyone can replicate.)
> 
> Ideally, TTFs intended for desktop users (and thus the ones intended for
> Google Fonts) should have both KERN and GPOS tables.
> 
> Given all of the above, we currently treat kerning on a v0 kern table
> as a good-to-have (but optional) feature.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1675
> See also: https://github.com/fonttools/fontbakery/issues/3148
> See also: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Font does not declare an optional &quot;kern&quot; table.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does the font have any invalid feature tags? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-layout-valid-feature-tags">opentype/layout_valid_feature_tags</a></summary>
    <div>


> 
> Incorrect tags can be indications of typos, leftover debugging code or
> questionable approaches, or user error in the font editor. Such typos can
> cause features and language support to fail to work as intended.
> 
> Font vendors may use private tags to identify private features. These tags
> must be four uppercase letters (A-Z) with no punctuation, spaces, or numbers.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3355





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does the font have any invalid language tags? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-layout-valid-language-tags">opentype/layout_valid_language_tags</a></summary>
    <div>


> 
> Incorrect language tags can be indications of typos, leftover debugging code
> or questionable approaches, or user error in the font editor. Such typos can
> cause features and language support to fail to work as intended.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3355





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does the font have any invalid script tags? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-layout-valid-script-tags">opentype/layout_valid_script_tags</a></summary>
    <div>


> 
> Incorrect script tags can be indications of typos, leftover debugging code
> or questionable approaches, or user error in the font editor. Such typos can
> cause features and language support to fail to work as intended.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3355





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does the number of glyphs in the loca table match the maxp table? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-loca-maxp-num-glyphs">opentype/loca/maxp_num_glyphs</a></summary>
    <div>


> 
> The 'maxp' table contains various statistics about the font, including the
> number of glyphs in the font. The 'loca' table contains the offsets to the
> locations of the glyphs in the font. The number of offsets in the 'loca' table
> should match the number of glyphs in the 'maxp' table. A failure here indicates
> a problem with the font compiler.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking head.macStyle value. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-mac-style">opentype/mac_style</a></summary>
    <div>


> 
> The values of the flags on the macStyle entry on the 'head' OpenType table
> that describe whether a font is bold and/or italic must be coherent with the
> actual style of the font as inferred by its filename.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>head macStyle ITALIC bit is properly set.</p>
 



* ✅ **PASS** <p>head macStyle BOLD bit is properly set.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> MaxAdvanceWidth is consistent with values in the Hmtx and Hhea tables? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-maxadvancewidth">opentype/maxadvancewidth</a></summary>
    <div>


> 
> The 'hhea' table contains a field which specifies the maximum
> advance width. This value should be consistent with the maximum
> advance width of all glyphs specified in the 'hmtx' table.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking correctness of monospaced metadata. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-monospace">opentype/monospace</a></summary>
    <div>


> 
> There are various metadata in the OpenType spec to specify if a font is
> monospaced or not. If the font is not truly monospaced, then no monospaced
> metadata should be set (as sometimes they mistakenly are...)
> 
> Requirements for monospace fonts:
> 
> * post.isFixedPitch - "Set to 0 if the font is proportionally spaced,
> non-zero if the font is not proportionally spaced (monospaced)"
> (https://www.microsoft.com/typography/otspec/post.htm)
> 
> * hhea.advanceWidthMax must be correct, meaning no glyph's width value
> is greater. (https://www.microsoft.com/typography/otspec/hhea.htm)
> 
> * OS/2.panose.bProportion must be set to 9 (monospace) on latin text fonts.
> 
> * OS/2.panose.bSpacing must be set to 3 (monospace) on latin hand written
> or latin symbol fonts.
> 
> * Spec says: "The PANOSE definition contains ten digits each of which currently
> describes up to sixteen variations. Windows uses bFamilyType, bSerifStyle
> and bProportion in the font mapper to determine family type. It also uses
> bProportion to determine if the font is monospaced."
> (https://www.microsoft.com/typography/otspec/os2.htm#pan
> https://monotypecom-test.monotype.de/services/pan2)
> 
> * OS/2.xAvgCharWidth must be set accurately.
> "OS/2.xAvgCharWidth is used when rendering monospaced fonts,
> at least by Windows GDI"
> (http://typedrawers.com/discussion/comment/15397/#Comment_15397)
> 
> Also we should report an error for glyphs not of average width.
> 
> 
> Please also note:
> 
> Thomas Phinney told us that a few years ago (as of December 2019), if you gave
> a font a monospace flag in Panose, Microsoft Word would ignore the actual
> advance widths and treat it as monospaced.
> 
> Source: https://typedrawers.com/discussion/comment/45140/#Comment_45140
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Font is not monospaced and all related metadata look good.</p>
 [code: good]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check name table for empty records. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-name-empty-records">opentype/name/empty_records</a></summary>
    <div>


> 
> Check the name table for empty records,
> as this can cause problems in Adobe apps.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2369





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does full font name begin with the font family name? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-name-match-familyname-fullfont">opentype/name/match_familyname_fullfont</a></summary>
    <div>


> 
> The FULL_FONT_NAME entry in the ‘name’ table should start with the same string
> as the Family Name (FONT_FAMILY_NAME, TYPOGRAPHIC_FAMILY_NAME or
> WWS_FAMILY_NAME).
> 
> If the Family Name is not included as the first part of the Full Font Name, and
> the user embeds the font in a document using a Microsoft Office app, the app
> will fail to render the font when it opens the document again.
> 
> NOTE: Up until version 1.5, the OpenType spec included the following exception
> in the definition of Full Font Name:
> 
> "An exception to the [above] definition of Full font name is for Microsoft
> platform strings for CFF OpenType fonts: in this case, the Full font name
> string must be identical to the PostScript FontName in the CFF Name INDEX."
> 
> https://docs.microsoft.com/en-us/typography/opentype/otspec150/name#name-ids
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Name table ID 6 (PostScript name) must be consistent across platforms. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-name-postscript-name-consistency">opentype/name/postscript_name_consistency</a></summary>
    <div>


> 
> The PostScript name entries in the font's 'name' table should be
> consistent across platforms.
> 
> This is the TTF/CFF2 equivalent of the CFF 'name/postscript_vs_cff' check.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2394





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check for points out of bounds. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-points-out-of-bounds">opentype/points_out_of_bounds</a></summary>
    <div>


> 
> The glyf table specifies a bounding box for each glyph. This check
> ensures that all points in all glyph paths are within the bounding
> box. Glyphs with out-of-bounds points can cause rendering issues in
> some software, and should be corrected.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/735





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> PostScript name follows OpenType specification requirements? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-postscript-name">opentype/postscript_name</a></summary>
    <div>


> 
> The PostScript name is used by some applications to identify the font.
> It should only consist of characters from the set A-Z, a-z, 0-9, and hyphen.
> 
> 




> Original proposal: https://github.com/miguelsousa/openbakery/issues/62





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Font has correct post table version? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-post-table-version">opentype/post_table_version</a></summary>
    <div>


> 
> Format 2.5 of the 'post' table was deprecated in OpenType 1.3 and
> should not be used.
> 
> According to Thomas Phinney, the possible problem with post format 3
> is that under the right combination of circumstances, one can generate
> PDF from a font with a post format 3 table, and not have accurate backing
> store for any text that has non-default glyphs for a given codepoint.
> 
> It will look fine but not be searchable. This can affect Latin text with
> high-end typography, and some complex script writing systems, especially
> with higher-quality fonts. Those circumstances generally involve creating
> a PDF by first printing a PostScript stream to disk, and then creating a
> PDF from that stream without reference to the original source document.
> There are some workflows where this applies,but these are not common
> use cases.
> 
> Apple recommends against use of post format version 4 as "no longer
> necessary and should be avoided". Please see the Apple TrueType reference
> documentation for additional details.
> 
> https://developer.apple.com/fonts/TrueType-Reference-Manual/RM06/Chap6post.html
> 
> Acceptable post format versions are 2 and 3 for TTF and OTF CFF2 builds,
> and post format 3 for CFF builds.
> 




> Original proposal: https://github.com/google/fonts/issues/215
> See also: https://github.com/fonttools/fontbakery/issues/2638
> See also: https://github.com/fonttools/fontbakery/issues/3635
> See also: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Font has an acceptable post format 2.0 table version.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking direction of slnt axis angles. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-slant-direction">opentype/slant_direction</a></summary>
    <div>


> 
> The 'slnt' axis values are defined as negative values for a clockwise (right)
> lean, and positive values for counter-clockwise lean. This is counter-intuitive
> for many designers who are used to think of a positive slant as a lean to
> the right.
> 
> This check ensures that the slant axis direction is consistent with the specs.
> 
> https://docs.microsoft.com/en-us/typography/opentype/spec/dvaraxistag_slnt
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3910





* ✅ **PASS** <p>Font has no slnt axis</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking unitsPerEm value is reasonable. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-unitsperem">opentype/unitsperem</a></summary>
    <div>


> 
> According to the OpenType spec:
> 
> The value of unitsPerEm at the head table must be a value
> between 16 and 16384. Any value in this range is valid.
> 
> In fonts that have TrueType outlines, a power of 2 is recommended
> as this allows performance optimizations in some rasterizers.
> 
> But 1000 is a commonly used value. And 2000 may become
> increasingly more common on Variable Fonts.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Validates that all of the instance records in a given font have distinct data. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-distinct-instance-records">opentype/varfont/distinct_instance_records</a></summary>
    <div>


> 
> According to the 'fvar' documentation in OpenType spec v1.9
> https://docs.microsoft.com/en-us/typography/opentype/spec/fvar
> 
> All of the instance records in a font should have distinct coordinates
> and distinct subfamilyNameID and postScriptName ID values. If two or more
> records share the same coordinates, the same nameID values or the same
> postScriptNameID values, then all but the first can be ignored.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3706





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Validate foundry-defined design-variation axis tag names. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-foundry-defined-tag-name">opentype/varfont/foundry_defined_tag_name</a></summary>
    <div>


> 
> According to the OpenType spec's syntactic requirements for
> foundry-defined design-variation axis tags available at
> https://learn.microsoft.com/en-us/typography/opentype/spec/dvaraxisreg
> 
> Foundry-defined tags must begin with an uppercase letter
> and must use only uppercase letters or digits.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4043





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Validates that all of the instance records in a given font have the same size. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-same-size-instance-records">opentype/varfont/same_size_instance_records</a></summary>
    <div>


> 
> According to the 'fvar' documentation in OpenType spec v1.9
> https://docs.microsoft.com/en-us/typography/opentype/spec/fvar
> 
> All of the instance records in a given font must be the same size, with
> all either including or omitting the postScriptNameID field. [...]
> If the value is 0xFFFF, then the value is ignored, and no PostScript name
> equivalent is provided for the instance.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3705





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> All fvar axes have a correspondent Axis Record on STAT table? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-STAT-axis-record-for-each-axis">opentype/varfont/STAT_axis_record_for_each_axis</a></summary>
    <div>


> 
> According to the OpenType spec, there must be an Axis Record
> for every axis defined in the fvar table.
> 
> https://docs.microsoft.com/en-us/typography/opentype/spec/stat#axis-records
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3017





* ✅ **PASS** <p>STAT table has all necessary Axis Records.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Validates subfamilyNameID and postScriptNameID for the default instance record <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-valid-default-instance-nameids">opentype/varfont/valid_default_instance_nameids</a></summary>
    <div>


> 
> According to the 'fvar' documentation in OpenType spec v1.9.1
> https://docs.microsoft.com/en-us/typography/opentype/spec/fvar
> 
> The default instance of a font is that instance for which the coordinate
> value of each axis is the defaultValue specified in the corresponding
> variation axis record. An instance record is not required for the default
> instance, though an instance record can be provided. When enumerating named
> instances, the default instance should be enumerated even if there is no
> corresponding instance record. If an instance record is included for the
> default instance (that is, an instance record has coordinates set to default
> values), then the nameID value should be set to either 2 or 17 or to a
> name ID with the same value as name ID 2 or 17. Also, if a postScriptNameID is
> included in instance records, and the postScriptNameID value should be set
> to 6 or to a name ID with the same value as name ID 6.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3708





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Validates that all of the name IDs in an instance record are within the correct range <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-valid-nameids">opentype/varfont/valid_nameids</a></summary>
    <div>


> 
> According to the 'fvar' documentation in OpenType spec v1.9
> https://docs.microsoft.com/en-us/typography/opentype/spec/fvar
> 
> The axisNameID field provides a name ID that can be used to obtain strings
> from the 'name' table that can be used to refer to the axis in application
> user interfaces. The name ID must be greater than 255 and less than 32768.
> 
> The postScriptNameID field provides a name ID that can be used to obtain
> strings from the 'name' table that can be treated as equivalent to name
> ID 6 (PostScript name) strings for the given instance. Values of 6 and
> "undefined" can be used; otherwise, values must be greater than 255 and
> less than 32768.
> 
> The subfamilyNameID field provides a name ID that can be used to obtain
> strings from the 'name' table that can be treated as equivalent to name
> ID 17 (typographic subfamily) strings for the given instance. Values of
> 2 or 17 can be used; otherwise, values must be greater than 255 and less
> than 32768.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3702
> See also: https://github.com/fonttools/fontbakery/issues/3703





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking if OS/2 usWeightClass matches fvar. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-weight-class-fvar">opentype/weight_class_fvar</a></summary>
    <div>


> 
> According to Microsoft's OT Spec the OS/2 usWeightClass
> should match the fvar default value.
> 




> Original proposal: https://github.com/googlefonts/gftools/issues/477





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check if OS/2 xAvgCharWidth is correct. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-xavgcharwidth">opentype/xavgcharwidth</a></summary>
    <div>


> 
> The OS/2.xAvgCharWidth field is used to calculate the width of a string of
> characters. It is the average width of all non-zero width glyphs in the font.
> 
> This check ensures that the value is correct. A failure here may indicate
> a bug in the font compiler, rather than something that the designer can
> do anything about.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>OS/2 xAvgCharWidth value is correct.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check that Arabic spacing symbols U+FBB2–FBC1 aren't classified as marks. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#arabic-spacing-symbols">arabic_spacing_symbols</a></summary>
    <div>


> 
> Unicode has a few spacing symbols representing Arabic dots and other marks,
> but they are purposefully not classified as marks.
> 
> Many fonts mistakenly classify them as marks, making them unsuitable
> for their original purpose as stand-alone symbols to used in pedagogical
> contexts discussing Arabic consonantal marks.
> 




> Original proposal: https://github.com/googlefonts/fontbakery/issues/4295





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check if uppercase glyphs are vertically centered. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#caps-vertically-centered">caps_vertically_centered</a></summary>
    <div>


> 
> This check suggests one possible approach to designing vertical metrics,
> but can be ingnored if you follow a different approach.
> In order to center text in buttons, lists, and grid systems
> with minimal additional CSS work, the uppercase glyphs should be
> vertically centered in the em box.
> This check mainly applies to Latin, Greek, Cyrillic, and other similar scripts.
> For non-latin scripts like Arabic, this check might not be applicable.
> There is a detailed description of this subject at:
> https://x.com/romanshamin_en/status/1562801657691672576
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4139





* ✅ **PASS** <p>Uppercase glyphs are vertically centered in the em box.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Color layers should have a minimum brightness. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#color-cpal-brightness">color_cpal_brightness</a></summary>
    <div>


> 
> Layers of a COLRv0 font should not be too dark or too bright. When layer colors
> are set explicitly, they can't be changed and they may turn out illegible
> against dark or bright backgrounds.
> 
> While traditional color-less fonts can be colored in design apps or CSS, a
> black color definition in a COLRv0 font actually means that that layer will be
> rendered in black regardless of the background color. This leads to text
> becoming invisible against a dark background, for instance when using a dark
> theme in a web browser or operating system.
> 
> This check ensures that layer colors are at least 10% bright and at most 90%
> bright, when not already set to the current color (0xFFFF).
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3908





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does font file include unacceptable control character glyphs? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#control-chars">control_chars</a></summary>
    <div>


> 
> Use of some unacceptable control characters in the U+0000 - U+001F range can
> lead to rendering issues on some platforms.
> 
> Acceptable control characters are defined as .null (U+0000) and
> CR (U+000D) for this check.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2430





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Put an empty glyph on GID 1 right after the .notdef glyph for COLRv0 fonts. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#empty-glyph-on-gid1-for-colrv0">empty_glyph_on_gid1_for_colrv0</a></summary>
    <div>


> 
> A rendering bug in Windows 10 paints whichever glyph is on GID 1 on top of
> some glyphs, colored or not. This only occurs for COLR version 0 fonts.
> 
> Having a glyph with no contours on GID 1 is a practical workaround for that.
> 
> See https://github.com/googlefonts/gftools/issues/609
> 




> Original proposal: https://github.com/googlefonts/gftools/issues/609
> See also: https://github.com/fonttools/fontbakery/pull/3905





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> All name entries referenced by fvar instances exist on the name table? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#fvar-name-entries">fvar_name_entries</a></summary>
    <div>


> 
> The purpose of this check is to make sure that all name entries referenced
> by variable font instances do exist in the name table.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2069





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure files are not too large. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#file-size">file_size</a></summary>
    <div>


> 
> Serving extremely large font files causes usability issues.
> This check ensures that file sizes are reasonable.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3320





* ✅ **PASS** <p>Font had a reasonable file size</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Do we have the latest version of FontBakery installed? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#fontbakery-version">fontbakery_version</a></summary>
    <div>


> 
> Running old versions of FontBakery can lead to a poor report which may
> include false WARNs and FAILs due do bugs, as well as outdated
> quality assurance criteria.
> 
> Older versions will also not report problems that are detected by new checks
> added to the tool in more recent updates.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2093





* ✅ **PASS** <p>FontBakery is up-to-date.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Familyname must be unique according to namecheck.fontdata.com <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#fontdata-namecheck">fontdata_namecheck</a></summary>
    <div>


> 
> We need to check names are not already used, and today the best place to check
> that is http://namecheck.fontdata.com
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/494





* ✅ **PASS** <p>Font familyname seems to be unique.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure that the font can be rasterized by FreeType. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#freetype-rasterizer">freetype_rasterizer</a></summary>
    <div>


> 
> Malformed fonts can cause FreeType to crash.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3642





* ✅ **PASS** <p>Font can be rasterized by FreeType.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure no GPOS7 lookups are present. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#gpos7">gpos7</a></summary>
    <div>


> 
> Versions of fonttools >=4.14.0 (19 August 2020) perform an optimisation on
> chained contextual lookups, expressing GSUB6 as GSUB5 and GPOS8 and GPOS7
> where possible (when there are no suffixes/prefixes for all rules in
> the lookup).
> 
> However, makeotf has never generated these lookup types and they are rare
> in practice. Perhaps because of this, Mac's CoreText shaper does not correctly
> interpret GPOS7, meaning that these lookups will be ignored by the shaper,
> and fonts containing these lookups will have unintended positioning errors.
> 
> To fix this warning, rebuild the font with a recent version of fonttools.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3643





* ✅ **PASS** <p>Font has no GPOS7 lookups</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Does GPOS table have kerning information? This check skips monospaced fonts as defined by post.isFixedPitch value <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#gpos-kerning-info">gpos_kerning_info</a></summary>
    <div>


> 
> Well-designed fonts use kerning to improve the spacing between
> specific pairs of glyphs. This check ensures that the font has
> kerning information in the GPOS table. It can be ignored if the
> design or writing system does not require kerning.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check that legacy accents aren't used in composite glyphs. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#legacy-accents">legacy_accents</a></summary>
    <div>


> 
> Legacy accents should not have anchors and should have positive width.
> They are often used independently of a letter, either as a placeholder
> for an expected combined mark+letter combination in MacOS, or separately.
> For instance, U+00B4 (ACUTE ACCENT) is often mistakenly used as an apostrophe,
> U+0060 (GRAVE ACCENT) is used in Markdown to notify code blocks,
> and ^ is used as an exponential operator in maths.
> 




> Original proposal: https://github.com/googlefonts/fontbakery/issues/4310





* ✅ **PASS** <p>Looks good!</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking Vertical Metric Linegaps. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#linegaps">linegaps</a></summary>
    <div>


> 
> The LineGap value is a space added to the line height created by the union
> of the (typo/hhea)Ascender and (typo/hhea)Descender. It is handled differently
> according to the environment.
> 
> This leading value will be added above the text line in most desktop apps.
> It will be shared above and under in web browsers, and ignored in Windows
> if Use_Typo_Metrics is disabled.
> 
> For better linespacing consistency across platforms,
> (typo/hhea)LineGap values must be 0.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4133
> See also: https://googlefonts.github.io/gf-guide/metrics.html





* ✅ **PASS** <p>OS/2 sTypoLineGap and hhea lineGap are both 0.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure small caps glyphs are available. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#missing-small-caps-glyphs">missing_small_caps_glyphs</a></summary>
    <div>


> 
> Ensure small caps glyphs are available if
> a font declares smcp or c2sc OT features.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3154





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Are there disallowed characters in the NAME table? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#name-char-restrictions">name/char_restrictions</a></summary>
    <div>


> 
> The OpenType spec requires a subset of ASCII
> (any printable characters except "[]{}()<>/%") for
> POSTSCRIPT_NAME (nameID 6),
> POSTSCRIPT_CID_NAME (nameID 20), and
> an even smaller subset ("a-zA-Z0-9") for
> VARIATIONS_POSTSCRIPT_NAME_PREFIX (nameID 25).
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1718
> See also: https://github.com/fonttools/fontbakery/issues/1663
> See also: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Combined length of family and style must not exceed 32 characters. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#name-family-and-style-max-length">name/family_and_style_max_length</a></summary>
    <div>


> 
> This check ensures that the length of name table entries is not
> too long, as this causes problems in some environments.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1488
> See also: https://github.com/fonttools/fontbakery/issues/2179





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Name table records must not have trailing spaces. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#name-trailing-spaces">name/trailing_spaces</a></summary>
    <div>


> 
> This check ensures that no entries in the name table end in
> spaces; trailing spaces, particularly in font names, can be
> confusing to users. In most cases this can be fixed by
> removing trailing spaces from the metadata fields in the font
> editor.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2417





* ✅ **PASS** <p>No trailing spaces on name table entries.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Description strings in the name table must not contain copyright info. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#name-no-copyright-on-description">name/no_copyright_on_description</a></summary>
    <div>


> 
> The name table in a font file contains strings about the font;
> there are entries for a copyright field and a description. If the
> copyright entry is being used correctly, then there should not
> be any copyright information in the description entry.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure glyphs do not have components which are themselves components. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#nested-components">nested_components</a></summary>
    <div>


> 
> There have been bugs rendering variable fonts with nested components.
> Additionally, some static fonts with nested components have been reported
> to have rendering and printing issues.
> 
> For more info, see:
> * https://github.com/fonttools/fontbakery/issues/2961
> * https://github.com/arrowtype/recursive/issues/412
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2961





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure font doesn't have Mac name table entries (platform=1). <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#no-mac-entries">no_mac_entries</a></summary>
    <div>


> 
> Mac name table entries are not needed anymore. Even Apple stopped producing
> name tables with platform 1. Please see for example the following system font:
> 
> /System/Library/Fonts/SFCompact.ttf
> 
> Also, Dave Opstad, who developed Apple's TrueType specifications, told
> Olli Meier a couple years ago (as of January/2022) that these entries are
> outdated and should not be produced anymore.
> 




> Original proposal: https://github.com/googlefonts/gftools/issues/469





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking OS/2 Metrics match hhea Metrics. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#os2-metrics-match-hhea">os2_metrics_match_hhea</a></summary>
    <div>


> 
> OS/2 and hhea vertical metric values should match. This will produce the
> same linespacing on Mac, GNU+Linux and Windows.
> 
> - Mac OS X uses the hhea values.
> - Windows uses OS/2 or Win, depending on the OS or fsSelection bit value.
> 
> When OS/2 and hhea vertical metrics match, the same linespacing results on
> macOS, GNU+Linux and Windows. Note that fixing this issue in a previously
> released font may cause reflow in user documents and unhappy users.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>OS/2.sTypoAscender/Descender values match hhea.ascent/descent.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking with ots-sanitize. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#ots">ots</a></summary>
    <div>


> 
> The OpenType Sanitizer (OTS) is a tool that checks that the font is
> structually well-formed and passes various sanity checks. It is used by
> many web browsers to check web fonts before using them; fonts which fail
> such checks are blocked by browsers.
> 
> This check runs OTS on the font and reports any errors or warnings that
> it finds.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check there are no overlapping path segments <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#overlapping-path-segments">overlapping_path_segments</a></summary>
    <div>


> 
> Some rasterizers encounter difficulties when rendering glyphs with
> overlapping path segments.
> 
> A path segment is a section of a path defined by two on-curve points.
> When two segments share the same coordinates, they are considered
> overlapping.
> 




> Original proposal: https://github.com/google/fonts/issues/7594#issuecomment-2401909084





* ✅ **PASS** <p>No overlapping path segments found.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Font has the proper sfntVersion value? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#sfnt-version">sfnt_version</a></summary>
    <div>


> 
> OpenType fonts that contain TrueType outlines should use the value of 0x00010000
> for the sfntVersion. OpenType fonts containing CFF data (version 1 or 2) should
> use 0x4F54544F ('OTTO', when re-interpreted as a Tag) for sfntVersion.
> 
> Fonts with the wrong sfntVersion value are rejected by FreeType.
> 
> https://docs.microsoft.com/en-us/typography/opentype/spec/otff#table-directory
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3388





* ✅ **PASS** <p>Font has the correct sfntVersion value.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check correctness of STAT table strings <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#STAT-strings">STAT_strings</a></summary>
    <div>


> 
> On the STAT table, the "Italic" keyword must not be used on AxisValues
> for variation axes other than 'ital'.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2863





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check tabular widths don't have kerning. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#tabular-kerning">tabular_kerning</a></summary>
    <div>


> 
> Tabular glyphs should not have kerning, as they are meant to be used in tables.
> 
> This check looks for kerning in:
> - all glyphs in a font in combination with tabular numerals;
> - tabular symbols in combination with tabular numerals.
> 
> "Tabular symbols" is defined as:
> - for fonts with a "tnum" feature, all "tnum" substitution target glyphs;
> - for fonts without a "tnum" feature, all glyphs that have the same width
> as the tabular numerals, but limited to numbers, math and currency symbols.
> 
> This check may produce false positives for fonts with no "tnum" feature
> and with equal-width numerals (and other same-width symbols) that are
> not intended to be used as tabular numerals.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4440





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking with fontTools.ttx <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#ttx-roundtrip">ttx_roundtrip</a></summary>
    <div>


> 
> One way of testing whether or not fonts are well-formed at the
> binary level is to convert them to TTX and then back to binary. Structural
> problems within the binary font will show up as errors during conversion.
> This is not necessarily something that a designer will be able to address
> but is evidence of a potential bug in the font compiler used to generate
> the binary.




> Original proposal: https://github.com/fonttools/fontbakery/issues/1763





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking that the typoAscender exceeds the yMax of the /Agrave. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#typoascender-exceeds-Agrave">typoascender_exceeds_Agrave</a></summary>
    <div>


> 
> MacOS uses OS/2.sTypoAscender/Descender values to determine the line height
> of a font. If the sTypoAscender value is smaller than the maximum height of
> the uppercase /Agrave, the font’s sTypoAscender value is ignored, and a very
> tall line height is used instead.
> 
> This happens on a per-font, per-style basis, so it’s possible for a font to
> have a good sTypoAscender value in one style but not in another. This can
> lead to inconsistent line heights across a typeface family.
> 
> So, it is important to ensure that the sTypoAscender value is greater than
> the maximum height of the uppercase /Agrave in all styles of a type family.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3170





* ✅ **PASS** <p>OS/2.sTypoAscender value is greater than the yMax of /Agrave.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Font contains unique glyph names? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#unique-glyphnames">unique_glyphnames</a></summary>
    <div>


> 
> Duplicate glyph names prevent font installation on Mac OS X.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Glyph names are all unique.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Are there unwanted Apple tables? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#unwanted-aat-tables">unwanted_aat_tables</a></summary>
    <div>


> 
> Apple's TrueType reference manual [1] describes SFNT tables not in the
> Microsoft OpenType specification [2] and these can sometimes sneak into final
> release files.
> 
> This check ensures fonts only have OpenType tables.
> 
> [1] https://developer.apple.com/fonts/TrueType-Reference-Manual/RM06/Chap6.html
> [2] https://docs.microsoft.com/en-us/typography/opentype/spec/
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2190





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Are there unwanted tables? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#unwanted-tables">unwanted_tables</a></summary>
    <div>


> 
> Some font editors store source data in their own SFNT tables, and these
> can sometimes sneak into final release files, which should only have
> OpenType spec tables.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>There are no unwanted tables.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Glyph names are all valid? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#valid-glyphnames">valid_glyphnames</a></summary>
    <div>


> 
> Microsoft's recommendations for OpenType Fonts states the following:
> 
> 'NOTE: The PostScript glyph name must be no longer than 31 characters,
> include only uppercase or lowercase English letters, European digits,
> the period or the underscore, i.e. from the set `[A-Za-z0-9_.]` and
> should start with a letter, except the special glyph name `.notdef`
> which starts with a period.'
> 
> https://learn.microsoft.com/en-us/typography/opentype/otspec181/recom#-post--table
> 
> 
> In practice, though, particularly in modern environments, glyph names
> can be as long as 63 characters.
> 
> According to the "Adobe Glyph List Specification" available at:
> 
> https://github.com/adobe-type-tools/agl-specification
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2832
> See also: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Glyph names are all valid.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check variable font instances don't have duplicate names <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-duplicate-instance-names">varfont/duplicate_instance_names</a></summary>
    <div>


> 
> This check's purpose is to detect duplicate named instances names in a
> given variable font.
> 
> Repeating instance names may be the result of instances for several VF axes
> defined in `fvar`, but in some setups only weight+italic tokens are used
> in instance names, so they end up repeating.
> 
> Only a base set of fonts for the most default representation of the
> family can be defined through instances in the `fvar` table, all other
> instances will have to be left to access through the `STAT` table.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2986





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure the font's instances are in the correct order. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-instances-in-order">varfont/instances_in_order</a></summary>
    <div>


> 
> Ensure that the fvar table instances are in ascending order of weight.
> Some software, such as Canva, displays the instances in the order they
> are defined in the fvar table, which can lead to confusion if the
> instances are not in order of weight.
> 




> Original proposal: https://github.com/googlefonts/fontbakery/issues/3334





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure VFs do not contain (yet) the ital axis. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-unsupported-axes">varfont/unsupported_axes</a></summary>
    <div>


> 
> The 'ital' axis is not supported yet in Google Chrome.
> 
> For the time being, we need to ensure that VFs do not contain this axis.
> Once browser support is better, we can deprecate this check.
> 
> For more info regarding browser support, see:
> https://arrowtype.github.io/vf-slnt-test/
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2866





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> VTT or Volt Source Data must not be present. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#vtt-volt-data">vtt_volt_data</a></summary>
    <div>


> 
> Check to make sure all the VTT source (TSI* tables) and
> VOLT stuff (TSIV and zz features & langsys records) are gone.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/4657





* ✅ **PASS** <p>TSI0 table not found</p>
 



* ✅ **PASS** <p>TSI1 table not found</p>
 



* ✅ **PASS** <p>TSI2 table not found</p>
 



* ✅ **PASS** <p>TSI3 table not found</p>
 



* ✅ **PASS** <p>TSI5 table not found</p>
 



* ✅ **PASS** <p>TSIC table not found</p>
 



* ✅ **PASS** <p>TSIV table not found</p>
 



* ✅ **PASS** <p>TSIP table not found</p>
 



* ✅ **PASS** <p>TSIS table not found</p>
 



* ✅ **PASS** <p>TSID table not found</p>
 



* ✅ **PASS** <p>TSIJ table not found</p>
 



* ✅ **PASS** <p>TSIB table not found</p>
 



* ✅ **PASS** <p>No VTT or Volt Source Data Found</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Font contains glyphs for whitespace characters? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#whitespace-glyphs">whitespace_glyphs</a></summary>
    <div>


> 
> The OpenType specification recommends that fonts should contain
> glyphs for the following whitespace characters:
> 
> - U+0020 SPACE
> - U+00A0 NO-BREAK SPACE
> 
> The space character is required for text processing, and the no-break
> space is useful to prevent line breaks at its position. It is also
> recommended to have a glyph for the tab character (U+0009) and the
> soft hyphen (U+00AD), but these are not mandatory.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Font contains glyphs for whitespace characters.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Whitespace glyphs have ink? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#whitespace-ink">whitespace_ink</a></summary>
    <div>


> 
> This check ensures that certain whitespace glyphs are empty.
> Certain text layout engines will assume that these glyphs are empty,
> and will not draw them; if they were in fact not designed to be
> empty, the result will be text layout that is not as expected.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>There is no whitespace glyph with ink.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Space and non-breaking space have the same width? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#whitespace-widths">whitespace_widths</a></summary>
    <div>


> 
> If the space and nbspace glyphs have different widths, then Google Workspace
> has problems with the font.
> 
> The nbspace is used to replace the space character in multiple situations in
> documents; such as the space before punctuation in languages that do that. It
> avoids the punctuation to be separated from the last word and go to next line.
> 
> This is automatic substitution by the text editors, not by fonts. It's also used
> by designers in text composition practice to create nicely shaped paragraphs.
> If the space and the nbspace are not the same width, it breaks the text
> composition of documents.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3843
> See also: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Space and non-breaking space have the same width.</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Is the CFF2 subr/gsubr call depth > 10? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-cff2-call-depth">opentype/cff2_call_depth</a></summary>
    <div>


> 
> Per "The CFF2 CharString Format", the "Subr nesting, stack limit" is 10.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2425





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cff2</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Does the font's CFF table top dict strings fit into the ASCII range? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-cff-ascii-strings">opentype/cff_ascii_strings</a></summary>
    <div>


> 
> All CFF Table top dict string chars should fit into the ASCII range.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4619





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cff</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Is the CFF subr/gsubr call depth > 10? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-cff-call-depth">opentype/cff_call_depth</a></summary>
    <div>


> 
> Per "The Type 2 Charstring Format, Technical Note #5177",
> the "Subr nesting, stack limit" is 10.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2425





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cff</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Does the font use deprecated CFF operators or operations? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-cff-deprecated-operators">opentype/cff_deprecated_operators</a></summary>
    <div>


> 
> The 'dotsection' operator and the use of 'endchar' to build accented characters
> from the Adobe Standard Encoding Character Set ("seac") are deprecated in CFF.
> Adobe recommends repairing any fonts that use these, especially endchar-as-seac,
> because a rendering issue was discovered in Microsoft Word with a font that
> makes use of this operation. The check treats that usage as a FAIL.
> There are no known ill effects of using dotsection, so that check is a WARN.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3033





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cff</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> CFF table FontName must match name table ID 6 (PostScript name). <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-name-postscript-vs-cff">opentype/name/postscript_vs_cff</a></summary>
    <div>


> 
> The PostScript name entries in the font's 'name' table should match
> the FontName string in the 'CFF ' table.
> 
> The 'CFF ' table has a lot of information that is duplicated in other tables.
> This information should be consistent across tables, because there's
> no guarantee which table an app will get the data from.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2229





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cff</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Checking OS/2 achVendID against configuration. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-vendor-id">opentype/vendor_id</a></summary>
    <div>


> 
> When a font project's Vendor ID is specified explicitly on FontBakery's
> configuration file, all binaries must have a matching vendor identifier
> value in the OS/2 table.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3941





* ⏩ **SKIP** <p>Add the <code>vendor_id</code> key to a <code>fontbakery.yaml</code> file on your font project directory to enable this check.
You'll also need to use the <code>--configuration</code> flag when invoking fontbakery.</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Each font in set of sibling families must have the same set of vertical metrics values. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#superfamily-vertical-metrics">superfamily/vertical_metrics</a></summary>
    <div>


> 
> We may want all fonts within a super-family (all sibling families) to have
> the same vertical metrics so their line spacing is consistent
> across the super-family.
> 
> This is an experimental extended version of the
> `family/vertical_metrics` check and for now it will only result in WARNs.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1487





* ⏩ **SKIP** <p>Sibling families were not detected.</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Check that glyph for U+0675 ARABIC LETTER HIGH HAMZA is not a mark. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#arabic-high-hamza">arabic_high_hamza</a></summary>
    <div>


> 
> Many fonts incorrectly treat ARABIC LETTER HIGH HAMZA (U+0675) as a variant of
> ARABIC HAMZA ABOVE (U+0654) and make it a combining mark of the same size.
> 
> But U+0675 is a base letter and should be a variant of ARABIC LETTER HAMZA
> (U+0621) but raised slightly above baseline.
> 
> Not doing so effectively makes the font useless for Jawi and
> possibly Kazakh as well.
> 




> Original proposal: https://github.com/googlefonts/fontbakery/issues/4290





* ⏩ **SKIP** <p>This check will only run on fonts that have both glyphs U+0621 and U+0675</p>
 [code: glyphs-missing]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Does the font contain chws and vchw features? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#cjk-chws-feature">cjk_chws_feature</a></summary>
    <div>


> 
> The W3C recommends the addition of chws and vchw features to CJK fonts
> to enhance the spacing of glyphs in environments which do not fully support
> JLREQ layout rules.
> 
> The chws_tool utility (https://github.com/googlefonts/chws_tool) can be used
> to add these features automatically.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3363





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_cjk_font</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Any CJK font should contain at least a minimal set of 150 CJK characters. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#cjk-not-enough-glyphs">cjk_not_enough_glyphs</a></summary>
    <div>


> 
> Kana has 150 characters and it's the smallest CJK writing system.
> 
> If a font contains less CJK glyphs than this writing system, we inform the
> user that some glyphs may be encoded incorrectly.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3214





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_claiming_to_be_cjk_font</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Check that format 12 cmap subtables are correctly constituted. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#cmap-format-12">cmap/format_12</a></summary>
    <div>


> 
> If a format 12 cmap table is used to address codepoints beyond the BMP,
> it should actually contain such codepoints. Additionally, it should also
> contain all characters mapped in the format 4 subtable.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/3681





* ⏩ **SKIP** <p>No format 12 subtables found</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Check if each glyph has the recommended amount of contours. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#contour-count">contour_count</a></summary>
    <div>


> 
> Visually QAing thousands of glyphs by hand is tiring. Most glyphs can only
> be constructured in a handful of ways. This means a glyph's contour count
> will only differ slightly amongst different fonts, e.g a 'g' could either
> be 2 or 3 contours, depending on whether its double story or single story.
> 
> However, a quotedbl should have 2 contours, unless the font belongs
> to a display family.
> 
> This check currently does not cover variable fonts because there's plenty
> of alternative ways of constructing glyphs with multiple outlines for each
> feature in a VarFont. The expected contour count data for this check is
> currently optimized for the typical construction of glyphs in static fonts.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ⏩ **SKIP** <p>Unfulfilled Conditions: not is_variable_font</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> PPEM must be an integer on hinted fonts. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#integer-ppem-if-hinted">integer_ppem_if_hinted</a></summary>
    <div>


> 
> Hinted fonts must have head table flag bit 3 set.
> 
> Per https://docs.microsoft.com/en-us/typography/opentype/spec/head,
> bit 3 of Head::flags decides whether PPEM should be rounded. This bit should
> always be set for hinted fonts.
> 
> Note:
> Bit 3 = Force ppem to integer values for all internal scaler math;
> May use fractional ppem sizes if this bit is clear;
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2338





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_hinted</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Check name table IDs 1, 2, 16, 17 to conform to Italic style. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#name-italic-names">name/italic_names</a></summary>
    <div>


> 
> This check ensures that several entries in the name table
> conform to the font's Upright or Italic style,
> namely IDs 1 & 2 as well as 16 & 17 if they're present.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3666





* ⏩ **SKIP** <p>Font is not Italic.</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Ensure indic fonts have the Indian Rupee Sign glyph. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#rupee">rupee</a></summary>
    <div>


> 
> Per Bureau of Indian Standards every font supporting one of the
> official Indian languages needs to include Unicode Character
> “₹” (U+20B9) Indian Rupee Sign.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2967





* ⏩ **SKIP** <p>Unfulfilled Conditions: is_indic_font</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Ensure 'smcp' (small caps) lookups are defined before ligature lookups in the 'GSUB' table. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#smallcaps-before-ligatures">smallcaps_before_ligatures</a></summary>
    <div>


> 
> OpenType small caps should be defined before ligature lookups to ensure
> proper functionality.
> 
> Rainer Erich Scheichelbauer (a.k.a. MekkaBlue) pointed out in a tweet
> (https://twitter.com/mekkablue/status/1297486769668132865) that the ordering
> of small caps and ligature lookups can lead to bad results such as the example
> he provided of the word "WAFFLES" in small caps, but with an unfortunate
> lowercase ffl ligature substitution.
> 
> This check attempts to detect this kind of mistake.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3020





* ⏩ **SKIP** <p>Font lacks 'smcp' or 'liga' features.</p>
 



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Checking STAT table entries in static fonts. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#STAT-in-statics">STAT_in_statics</a></summary>
    <div>


> 
> Adobe feature syntax allows for the definition of a STAT table. Fonts built
> with a hand-coded STAT table in feature syntax may be built either as static
> or variable, but will end up with the same STAT table.
> 
> This is a problem, because a STAT table which works on variable fonts
> will not be appropriate for static instances. The examples in the OpenType spec
> of non-variable fonts with a STAT table show that the table entries must be
> restricted to those entries which refer to the static font's position in
> the designspace. i.e. a Regular weight static should only have the following
> entry for the weight axis:
> 
> <AxisIndex value="0"/>
> <Flags value="2"/>  <!-- ElidableAxisValueName -->
> <ValueNameID value="265"/>  <!-- Regular -->
> <Value value="400.0"/>
> 
> However, if the STAT table intended for a variable font is compiled into a
> static, it will have many entries for this axis. In this case, Windows will
> read the first entry only, causing all instances to report themselves
> as "Thin Condensed".
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4149





* ⏩ **SKIP** <p>Unfulfilled Conditions: not is_variable_font</p>
 [code: unfulfilled-conditions]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Ensure VFs with duplexed axes do not vary horizontal advance. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-duplexed-axis-reflow">varfont/duplexed_axis_reflow</a></summary>
    <div>


> 
> Certain axes, such as grade (GRAD) or roundness (ROND), should not
> change any advanceWidth or kerning data across the font's design space.
> This is because altering the advance width of glyphs can cause text reflow.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/3187





* ⏩ **SKIP** <p>This font has no duplexed axes</p>
 [code: no-relevant-axes]



</div>
</details>
</div>
</details>

<details><summary>[12] Family checks</summary>
<div>
<details>
    <summary>✅ <b>PASS</b> Check that OS/2.fsSelection bold & italic settings are unique for each NameID1 <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-bold-italic-unique-for-nameid1">opentype/family/bold_italic_unique_for_nameid1</a></summary>
    <div>


> 
> Per the OpenType spec: name ID 1 'is used in combination with Font Subfamily
> name (name ID 2), and should be shared among at most four fonts that differ
> only in weight or style.
> 
> This four-way distinction should also be reflected in the OS/2.fsSelection
> field, using bits 0 and 5.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2388





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Verify that family names in the name table are consistent across all fonts in the family. Checks Typographic Family name (nameID 16) if present, otherwise uses Font Family name (nameID 1) <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-consistent-family-name">opentype/family/consistent_family_name</a></summary>
    <div>


> 
> Per the OpenType spec:
> 
> * "...many existing applications that use this pair of names assume that a
> Font Family name is shared by at most four fonts that form a font
> style-linking group"
> 
> * "For extended typographic families that includes fonts other than the
> four basic styles(regular, italic, bold, bold italic), it is strongly
> recommended that name IDs 16 and 17 be used in fonts to create an
> extended, typographic grouping."
> 
> * "If name ID 16 is absent, then name ID 1 is considered to be the
> typographic family name."
> 
> https://learn.microsoft.com/en-us/typography/opentype/spec/name
> 
> Fonts within a font family all must have consistent names
> in the Typographic Family name (nameID 16)
> or Font Family name (nameID 1), depending on which it uses.
> 
> Inconsistent font/typographic family names across fonts in a family
> can result in unexpected behaviors, such as broken style linking.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4112





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Make sure all font files have the same version value. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-equal-font-versions">opentype/family/equal_font_versions</a></summary>
    <div>


> 
> Within a family released at the same time, all members of the family
> should have the same version number in the head table.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Verify that each group of fonts with the same nameID 1 has maximum of 4 fonts. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-max-4-fonts-per-family-name">opentype/family/max_4_fonts_per_family_name</a></summary>
    <div>


> 
> Per the OpenType spec:
> 
> 'The Font Family name [...] should be shared among at most four fonts that
> differ only in weight or style [...]'
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/2372





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Fonts have consistent PANOSE family type? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-panose-familytype">opentype/family/panose_familytype</a></summary>
    <div>


> 
> The [PANOSE value](https://monotype.github.io/panose/) in the OS/2 table is a
> way of classifying a font based on its visual appearance and characteristics.
> 
> The first field in the PANOSE classification is the family type: 2 means Latin
> Text, 3 means Latin Script, 4 means Latin Decorative, 5 means Latin Symbol.
> This check ensures that within a family, all fonts have the same family type.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Fonts have consistent underline thickness? <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-family-underline-thickness">opentype/family/underline_thickness</a></summary>
    <div>


> 
> Dave C Lemon (Adobe Type Team) recommends setting the underline thickness to be
> consistent across the family.
> 
> If thicknesses are not family consistent, words set on the same line which have
> different styles look strange.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>Fonts have consistent underline thickness.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Check that family axis ranges are indentical <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-varfont-family-axis-ranges">opentype/varfont/family_axis_ranges</a></summary>
    <div>


> 
> Between members of a family (such as Roman & Italic),
> the ranges of variable axes must be identical.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4445





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Checking all files are in the same directory. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#family-single-directory">family/single_directory</a></summary>
    <div>


> 
> If the set of font files passed in the command line is not all in the
> same directory, then we warn the user since the tool will interpret the
> set of files as belonging to a single family (and it is unlikely that
> the user would store the files from a single family spreaded
> in several separate directories).
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/4829





* ✅ **PASS** <p>All files are in the same directory.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Each font in a family must have the same set of vertical metrics values. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#family-vertical-metrics">family/vertical_metrics</a></summary>
    <div>


> 
> We want all fonts within a family to have the same vertical metrics so
> their line spacing is consistent across the family.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/1487





* ✅ **PASS** <p>Vertical metrics are the same across the family.</p>
 



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Typographic Family name consistency. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#typographic-family-name">typographic_family_name</a></summary>
    <div>


> 
> Check whether Name ID 16 (Typographic Family name) is consistent
> across the set of fonts.
> 




> Original proposal: https://github.com/fonttools/fontbakery/pull/4657





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>✅ <b>PASS</b> Ensure that all variable font files have the same set of axes and axis ranges. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/universal.html#varfont-consistent-axes">varfont/consistent_axes</a></summary>
    <div>


> 
> In order to facilitate the construction of intuitive and friendly user
> interfaces, all variable font files in a given family should have the same set
> of variation axes. Also, each axis must have a consistent setting of min/max
> value ranges accross all the files.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2810





* ✅ **PASS** <p>All looks good!</p>
 [code: ok]



</div>
</details>

<details>
    <summary>⏩ <b>SKIP</b> Ensure VFs have 'ital' STAT axis. <a href="https://fontbakery.readthedocs.io/en/stable/fontbakery/checks/opentype.html#opentype-STAT-ital-axis">opentype/STAT/ital_axis</a></summary>
    <div>


> 
> Check that related Upright and Italic VFs have an
> 'ital' axis in the STAT table.
> 
> Since the STAT table can be used to create new instances, it is
> important to ensure that such an 'ital' axis be the last one
> declared in the STAT table so that the eventual naming of new
> instances follows the subfamily traditional scheme (RIBBI / WWS)
> where "Italic" is always last.
> 
> The 'ital' axis should also be strictly boolean, only accepting
> values of 0 (for Uprights) or 1 (for Italics). This usually works
> as a mechanism for selecting between two linked variable font files.
> 
> Also, the axis value name for uprights must be set as elidable.
> 




> Original proposal: https://github.com/fonttools/fontbakery/issues/2934
> See also: https://github.com/fonttools/fontbakery/issues/3668
> See also: https://github.com/fonttools/fontbakery/issues/3669





* ⏩ **SKIP** <p>Font {font.file} doesn't have an ital axis</p>
 



</div>
</details>
</div>
</details>




### Summary

| 💥 ERROR | ☠ FATAL | 🔥 FAIL | ⚠️ WARN | ⏩ SKIP | ℹ️ INFO | ✅ PASS | 🔎 DEBUG | 
| ---|---|---|---|---|---|---|---|
| 0 | 0 | 9 | 8 | 19 | 3 | 88 | 0 | 
| 0% | 0% | 7% | 6% | 15% | 2% | 69% | 0% | 


