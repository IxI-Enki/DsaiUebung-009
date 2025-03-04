<div align="center">

 ###### DsaiUebung-009--*Train your own LLM* : [Assignment <sup>(12.2.2025)</sup> ](https://github.com/IxI-Enki/DsaiUebung-009/blob/master/documentation/assignment.md)

<!-- #### Visit The [Github-page](https://github.com/IxI-Enki/DsaiUebung-009) ! -- <sub>by</sub>  ***Jan Ritt***
-->
</div>

---

#  [Teachable Machines](https://teachablemachine.withgoogle.com/) <br><sup><sup><u> Ascii-Box(Char)-Recognizer </u></sup></sub>
#### *The Idea*:<br>
  - *I wanted to make something maybe more useful than an LLM to differ between cat & dog pictures.*
  - Because on Teachable Machines the LLM training can be done based on picture- & audio-data,<br>
    > - *I choose to train it to recognize ASCII-Box-Characters[^1]*;<br>
    >   and then whole Boxes and their properties like 'closed-box', 'one-line-stroke-style', 'bold-line-style', 'irregular-box', ...[^2]
  - The first hurdle was to provide a good dataset for this - in size and variety - **DIY**.<br>
    > - *I coded an [application](https://github.com/IxI-Enki/DsaiUebung-009/blob/master/README.md#21-the-charifier---------my-c-application-for-testdata-creation) that can generate* **random boxchars** *in* **random RGB-colors**, *on random background-color:* <br>
    >   It prints each char in a consistent surrounding space, takes a screenshot with Skia from this sample and stores it as .png to feed them into the LLM afterwards.*
  - The LLM should be able to tell me if a drawn Ascii-box is a valid (eg. `closed` and `coherent`) box,<br>or if my box-creation-code needs some adjustments,<br>
    > - *This would be very helpful, in conjunction to normal unit-testing of each combination of box-/line-attributes,<br>
    >   to test my codebases creation and to provide a more robust ASCII-Box-Drawing-Solution, for my usecase.*
<!-- FOOTNOTES ------------------------------------------------------------ -->
[^1]: **All ASCII - Box - Characters**:<br>
╵ ╷ ╶ ╴ ╹ ╻ ╺ ╸ │ ┃ ║ ╽ ╿ ╎ ╏ ┆ ┇ ┊ ┋ ─ ━ ═ ╾ ╼ ╌ ╍ ┄ ┅ ┈ ┉
╭ ╮ ┌ ┐ ╰ ╯ └ ┘ ┍ ┑ ┎ ┒ ┕ ┙ ┖ ┚ ┏ ┓ ┗ ┛ ╒ ╕ ╓ ╖ ╘ ╛ ╙ ╜ ╔ ╗ ╚ ╝
├ ┤ ┝ ┥ ┟ ┧ ┞ ┦ ┢ ┪ ┡ ┩ ┠ ┨ ┣ ┫ ╞ ╡ ╟ ╢ ╠ ╣
┬ ┴ ┭ ┮ ┰ ┵ ┶ ┸ ┯ ┱ ┲ ┷ ┹ ┺ ┳ ┻ ╤ ╥ ╧ ╨ ╦  ╩
┼ ┽ ┾ ╀ ╁ ┿ ╂ ╪ ╫ ╃ ╄ ╅ ╆ ╇ ╈ ╉ ╊ ╋ ╬

[^2]: *The full implementation of the BoxDrawer and updated trainings-set is still in-development, yet.*
<!------------------------------------------------------------------------- -->


   ---

  #### *As I started coding my Boxdrawer, i found this paragraph on wikipedia and could not belive it at first:*<br>
  "*... However*, &nbsp; DOS line- and <mark>box-drawing characters</mark> are <u><mark>not ordered in any programmatic manner</mark></u>,
    *so calculating* <u>a <mark>particular</mark> character shape <mark>needs</mark> a <mark>look-up table</mark></u> ..." &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  <sub>source</sub> Wiki :<a href="https://en.wikipedia.org/wiki/Box-drawing_characters" title="takes you to wikipedia.com page on ASCII-Box-chars" target="_blank">Box-drawing-characters</a>

  ---

# 1.) Getting familliar with Teachable-Machines

On teachable machines you can train a large language model either on audio, or images.
  *I chose to use the image-variant*, which has this GUI on startup:<br>

<div align="center">

  <img src="/img/llm-teachablemachines-gui.png" alt="teachable-machines-picture-gui" width=60%>
</div>

The LLM can learn the difference between uploaded classes.
*In the first step, i wanted it to just to differ between alphanumeric-chars and the special ASCII-box-chars*.<br>

---

# 2.) Creating the Trainings-DataSets

To satisfy the "additional requirement" of the assignment - to implement the Model in our own project,
*I generated the needed trainings-data instead of using the trained model afterwards*.
  > *( Because it wasn't specified in the assignment, i assume that either side of the LLM pipeline would be fine. )*

  - ## 2.1.) '[The Charifier](https://github.com/IxI-Enki/xConsole_screen/tree/ascii-box-charifyer/Solution.Module/BoxCharifyer)' - <br> &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; <small><sup> My **C#**-Application for Testdata Creation</sup></small>
      - Comprehensive documentation can be found [ here ](https://github.com/IxI-Enki/xConsole_screen/blob/ascii-box-charifyer/Solution.Module/BoxCharifyer/README.md).
        > further notes can be found [here](https://github.com/IxI-Enki/DsaiUebung-009/blob/master/documentation/_api_readme.md)

      - ### *"Heart"* of the application - screencapturing with `SkiaSharp`:

        <div align="center">

          <img src="/img/dataset-creation-skiacode.png" alt="skiasharp" width=450px height=220px>
        </div><br><br><br>

      - ### Examples of the [final custom generated trainings-data](https://github.com/IxI-Enki/DsaiUebung-009/tree/master/trainings-sets):<br>
        > - *I generated <u>`500 variants`</u> of each of the <u>`200 Bockchars`</u> => `10.000 BoxChars`*.
        > - *And <u>`3400 alpha-numeric`</u> chars (also in random colors) as second trainings-set*.

        <div align="center">

           <span><img src="/img/e1.png" alt="example" width=100px height=200px><img src="/img/e2.png" alt="example" width=100px height=200px><img src="/img/e3.png" alt="example" width=100px height=200px><img src="/img/dataset-creation-files.png" alt="example" width=180px height=220px></span>
        </div>

---

# 3.) Training the Large Language Model

> To train the model, i <u>uploaded `13400` generated images</u> in total, which took a while..

<div align="center">

  <img src="/img/llm-trainings-setup.png" alt="" width=65%>
</div>

  - <details>
      <summary>
      <span><a style="color:royalblue">Peak</a> 'Under the Hood</u>'</span>

      </summary>


      <div align="center">

       | <img src="/img/llm-hood.png" alt="hood" width=400px> | <img src="/img/llm-loss.png" alt="loss" width=300px><br><img src="/img/llm-accuracy.png" alt="accuracy" width=300px> |
       |-|-|
      </div>
    </details>

  ---

# 4.) Testing the Capabilities of the Model

- There are no `black-white` sample-chars in the trainings set.

  >  <span>
  >  So I tried to take some screenshots from<br>normal console outputs,<br> varrying with x-y-offset.<br>
  >   <img src="/img/llm-testchar.png" alt="testchar" width=23px height=40px>
  >   </span>

<div align="center">

   <img src="/img/llm-test.png" alt="skiasharp" width=65%>
</div>

  > *Now it knows exactly how to differentiate the characters on screen at all times.*  🥳🎉🫱🏻‍🫲🏻💻

<div align="center">

### You can download the trained model [here]( https://github.com/IxI-Enki/DsaiUebung-009/blob/master/files/_ASCII-boxchar-Recognizer.tm) !

</div>
<!--
<div align="center">

|topic|screenshot|
|-|-|
|||
| | <img alt="llm-hood" src="img\llm-hood.png" width=500px> |
| |  |
| | <img alt="llm-loss" src="img\llm-loss.png" width=500px> |
| |  |
| | <img alt="llm-test" src="img\llm-test.png" width=500px> |
| |  |
| | <img alt="llm-accuracy" src="img\llm-accuracy.png" width=500px> |
| |  |
| | <img alt="llm-test-output" src="img\llm-test-output.png" width=220px> |
| |  |
| | <img alt="llm-trainings-setup" src="img\llm-trainings-setup.png" width=500px> |
| |  |
| | <img alt="dataset-creation-files" src="img\dataset-creation-files.png" width=300px> |
| |  |
| | <img alt="dataset-creation-skiacode" src="img\dataset-creation-skiacode.png" width=500px> |
| |  |
| | |
| |  |
|||



</div>
-->
<!-- images:
<img alt="" src="img\.png" width=500px>

<img alt="llm-hood" src="img\llm-hood.png" width=500px>
llm-hood.png
llm-hood
<img alt="llm-loss" src="img\llm-loss.png" width=500px>
llm-loss.png
llm-loss
<img alt="llm-test" src="img\llm-test.png" width=500px>
llm-test.png
llm-test
<img alt="llm-accuracy" src="img\llm-accuracy.png" width=500px>
llm-accuracy.png
llm-accuracy
<img alt="llm-test-output" src="img\llm-test-output.png" width=500px>
llm-test-output.png
llm-test-output
<img alt="llm-trainings-setup" src="img\llm-trainings-setup.png" width=500px>
llm-trainings-setup.png
llm-trainings-setup
<img alt="dataset-creation-files" src="img\dataset-creation-files.png" width=500px>
dataset-creation-files.png
dataset-creation-files
<img alt="dataset-creation-skiacode" src="img\dataset-creation-skiacode.png" width=500px>
dataset-creation-skiacode.png
dataset-creation-skiacode
<img alt="dataset-creation-output-test" src="img\dataset-creation-output-test.png" width=500px>
dataset-creation-output-test.png
dataset-creation-output-test
<img alt="dataset-creation-screen-to-image" src="img\dataset-creation-screen-to-image.png" width=500px>
dataset-creation-screen-to-image.png
dataset-creation-screen-to-image
-->
