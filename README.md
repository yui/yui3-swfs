yui3-swfs
=========

Source code for all Flash-based functionality from the YUI 3 project (https://github.com/yui/yui3). Projects wishing to use these features should compile and host their own SWFs.

You can compile the flash code several ways. Below is one way to do it using the mxmlc compiler available in the flex sdk. Feel free to submit a pull request with alternate methods.

The latest flex sdk is available here: http://flex.apache.org/index.html 

Example of how to compile io.swf
mxmlc -static-link-runtime-shared-libraries=true -output=io.swf as/io.as

Example of how to compile uploader.swf
mxmlc -static-link-runtime-shared-libraries=true -output=flashuploader.swf as/FlashUploader.as
