###### <p align="center">DsaiUebung-009-Ritt</p>
 
<div align="center">
  
   *Train your own LLM* : [Assignment <sup>(12.2.2025)</sup> ](https://github.com/IxI-Enki/DsaiUebung-009/blob/master/documentation/assignment.md)
</div>

---

# Teachable Machines <br><sup><sup><u> Ascii-Box(Char)-Recognizer </u></sup></sub>
#### *The Idea*:<br>
  - *I wanted to make something maybe more useful than an LLM to differ between cat & dog pictures.*  
  - Because on Teachable Machines only the training of LLMs based on picture-&audio-data is avaliable,<br>
    > - I choose to train the LLM to recognize ASCII-Box-Characters;<br>
    >   *and then whole Boxes and their properties like 'closed-box', 'one-line-stroke-style', 'bold-line-style', 'irregular-box', ...*
  - The first hurdle was to provide a good dataset for this - in size and variety - **DIY**.<br>
    > - I coded an application that can generate **random boxchars** in **random RGB-colors**, on random background-color:<br>
    >   *It prints each char in a consistent surrounding space, takes a screenshot with Skia from this sample and stores it as .png to feed them into the LLM afterwards.* 
  - The LLM should be able to tell me if a drawn Ascii-box is a valid (eg. closed and coherent) box,<br>
    or if my box-creation-code needs some adjustments,<br>
    > - *This would be very helpful, in conjunction to normal unit-testing of each combination of box-/line-attributes,<br>
    >   to test my codebases creation and to provide a more robust ASCII-Box-Drawing-Solution, for my usecase.*   

   ---

  #### *As I started coding my Boxdrawer, i found this paragraph on wikipedia and could not belive it at first:*<br>
  "  
   &nbsp; *... However*, &nbsp; DOS line- and <mark>box-drawing characters</mark> are <u><mark>not ordered in any programmatic manner</mark></u>,
   <br>&nbsp; *so calculating* <u>a <mark>particular</mark> character shape <mark>needs</mark> a <mark>look-up table</mark></u> &nbsp;...<br>  
    " &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <sub>source</sub> Wiki :<a href="https://en.wikipedia.org/wiki/Box-drawing_characters" title="takes you to wikipedia.com page on ASCII-Box-chars" target="_blank">Box-drawing-characters</a>

  ---  
  
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
| | <img alt="dataset-creation-output-test" src="img\dataset-creation-output-test.png" width=320px height=400px> |
| |  |
|||

### Examples of the custom generated trainings-data:<br>
| <img src="https://github.com/IxI-Enki/DsaiUebung-009/blob/master/trainings-sets/each-boxchar-x500-randomcolor/capture_2025-02-24_004606_173.png" alt="example" width=150px height=300px> | <img src="https://github.com/IxI-Enki/DsaiUebung-009/blob/master/trainings-sets/each-boxchar-x500-randomcolor/capture_2025-02-24_004726_421.png" alt="example" width=150px height=300px> | <img src="https://github.com/IxI-Enki/DsaiUebung-009/blob/master/trainings-sets/each-boxchar-x500-randomcolor/capture_2025-02-24_004811_012.png" alt="example" width=150px height=300px> |
|-|-|-|

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
