# DarkLabel

### Video/Image Labeling and Annotation Tool
This is a utility program that can label object bounding boxes with ID and name in videos and images. It also can be used to crop videos, sample traninig images in a video, and mosaic image region. Anyone can use it for non-commercial purposes.

### Download Executable
* [DarkLabel2.3.zip](https://github.com/darkpgmr/DarkLabel/releases/tag/darklabel2.3-release)
(currently, only binary executable can be downloaded)

![My image](https://github.com/darkpgmr/DarkLabel/blob/master/image/darklabel_gui.png)

### Main Features
* Video/image object labeling & annotation tool (bounding box with ID and label)
  * automatic object labeling by visual tracking (multi-target)
  * semi-automatic labeling by linear interpolation
  * user-configurable hotkeys and zoom in / zoom out support
  * user-configurable data formats (pascal voc, darket yolo, xml/txt, any other user-defined formats)
* Video splitting (into images) & image merging (into a video file) tool
* Video cropping tool (cut and save only the selected section in the video)
* Video/image privacy masking tool (mosaic the box area in the image)
* Windows only (32/64 bits)

### Program Configuration
The program can be configured by modifying [darklabel.yml](https://github.com/darkpgmr/DarkLabel/blob/master/darklabel.yml) attached in the zipped archive.
* define and modify data formats
* change hotkeys (frame navigation, action keys)
* change video/image export setting (video codec, frame rate, image format)
* set default save/load directory
* define class labels
* adjust GUI drawing (box width, box color, ...)


### Basic Instruction (How to Use)

	Arrow/PgUp/PgDn/Home/End: navigate image frames	
	
	Mouse: Left(create box), Right(cancel the most recently created box)
	Shift+Mouse: Left(modify box), Right(delete selected box/trajectory or all boxes)
	Shift+DoubleClick: modify box properties (label, ID, difficulty)
	
	DoubleClick: select/deselect box trajectory
	*box trajectory: boxes connected across frames with the same ID and label
	
	Ctrl+'+'/'-': zoom in/out
	Ctrl+Arrow: scroll zoomed window
	Ctrl+MouseWheel: zoom in/out
	Ctrl+MouseDrag: scroll zoomed window
	
	Enter: apply tracking (selected trajectories or newly created boxes only)
	Ctrl+'s': save gt	
	F1: show help

### Advanced Instruction
* Labeling by object tracking
  * By pressing 'Return' key, _newly created_ bounding boxes in the current frame are tracked in the next frame and labeled automatically.
    * _newly created boxes_: the boxes that are created after entering the frame.
  * If there are selected trajectories in the frame (object trajectory can be selected by double clicking a box), only the trajectory boxes are tracked (newly created boxes are not tracked).
  * If tracking is applied to trajectories, it first deletes their tail parts (connected trajectory boxes after the current frame) and then continue the tracking, keeping their IDs and labels. This functionality can be used to correct previous wrong tracking.
* Data Sampling/gathering
  * If you want to sample images in a video and save them (e.g. gathering training samples), draw dummy boxes on the images and then export the annotation results as images with the "no box drawing" option selected and the "labeled frames only" checked.
* Privacy Masking
  * draw boxes on the privacy area (e.g. human faces) and then export the annotation results with the "mosaic the box area" option selected.
* Full screen mode
  * do annotation in full screen mode in case the image is too large to show in your monitor (double click the title bar of image window). You also can utilize zoom in functionality.
* Don't forget to save your annotation results as often as possible. You can just press Ctrl+S.
