# JVDownloader
Just import this library into your java file and you can download any file from internet.

help you to download file using java

========================
@ How to use :

1. Create Object :
   
   		ex : JVDownloader downloadTask = new JVDownloader(url,path,fileName,fileExtension);
   
2. Start Download Task
	
		ex : downloadTask.start();
	
3. Pause Download Task
	
		ex : downloadTask.pause();

4. Resume Download Task
	
		ex : downloadTask.resume();

5. Cancel Download Task
	
		ex : downloadTask.stop();
	
Note : No deprecated methods have been used.
============================
@ If you want to check to download status (downloading ,failed or completed)

	ex : if(downloadTask.downloadStatus==0){
		  //then downloading	
	     }

	ex : if(downloadTask.downloadStatus==1){
		 //download completed
              }

	ex : if(downloadTask.downloadStatus==-1){
		 //then downloading failed
              }
			 
			 
Note :	You can bind the progressBar/progressIndecator  progressProperty
        with the progressProperty of downloadingTask
==============================	
@ How to bind the progressProperty of downloadTask in your code.

	ex : 
		ProgressIndicator p=new ProgressIndicator(); 
		p.progressProperty().bind(downloadTask.progressProperty());
	   
	ex : 
		ProgressBar p=new ProgressBar(); 
		p.progressProperty().bind(downloadTask.progressProperty());
	
==============================


EXAMPLE : JavaFX

    public void download(String url,String path,String fileName,String fileExtension){
   
       JVDownloader downloadTask=new JVDownloader(url,path,fileName,fileExtension);
    
	   ProgressIndicator p=new ProgressIndicator(); 
       p.progressProperty().bind(downloadTask.progressProperty());
      
       Button b1=new Button("Paluse");
       b1.setOnAction((ActionEvent event) -> {
           downloadTask.pause();
        });
		
       Button b2=new Button("Resume");
       b2.setOnAction((ActionEvent event) -> {
          downloadTask.resume();
       });
		
       Button b3=new Button("Cancel");
       b3.setOnAction((ActionEvent event) -> {
           downloadTask.stop();
        });
		
       HBox hb=new HBox();
       hb.getChildren().addAll(p,b1,b2,b3);
		
       mainContainer.getChildren().add(hb);    //mainContainer can be a VBox, where you want to display the all downloading task
       
       downloadTask.start();     
    }
