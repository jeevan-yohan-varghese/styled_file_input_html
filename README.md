# Styling an input type file in html
This is a sample project which explains how to style an file input using a label in html.

## Single file input

We have input which has type file and its display is set as none.  We use a label which acts as the input and we can style this label as we need.
````
<input type="file" style="display:none;" id="file_input_1">
<label for="file_input_1">Upload</label>
````
### Setting selected file name to label

Here we use javascript for setting the selected file name as the text of the label
```
var input = document.getElementById('file_input');
       
       input.addEventListener('change',function(e){
           
           var selectedFileName=e.target.value.split('\\').pop();
           
           document.getElementById('upld_lbl').innerHTML = selectedFileName;
           
           
       });
       
```
## Multiple Inputs

Here we have 3 file inputs.
```
<div id="inputs_container_main_div">
        <div class="input_container">
        
            <input id="file_input_1" type="file" style="display:none;" class="file_upload_input"/>
            <label for="file_input_1">Upload</label>
        </div>
        <div class="input_container">
        
            <input id="file_input_2" type="file" style="display:none;" class="file_upload_input"/>
            <label for="file_input_2">Upload</label>
        </div>
        <div class="input_container">
        
            <input id="file_input_3" type="file" style="display:none;" class="file_upload_input"/>
            <label for="file_input_3">Upload</label>
        </div>
            </div>
```
### Setting the selected file name to label

To avoid writing seperate event listeners for each input we use for loop and **nextElementSibling** method.  Make sure that you place the label immediately after the input. Otherwise this method won't work.  The maximum value of the loop is same as the number of inputs we have (here it is 3). Also all the inputs should have same class name (here it is **file_upload_input**)
```
       var inputs = document.querySelectorAll('.file_upload_input');
              for (i = 0; i < 3; i++) {       //Looping the inputs so that it would set event listener for all the inputs.
                                              //The maximum value loop should be the number of inputs that you have(here it is 3)
                  inputs[i].addEventListener('change', function (e) {

                      

                      var selectedFileName = e.target.value.split('\\').pop();///Getting the selected file name
                      
                      
                    
                      document.getElementById(e.target.id).nextElementSibling.innerHTML = selectedFileName;///Setting the selected file name to the label
                      

                      
                  }
             );
              }
```
