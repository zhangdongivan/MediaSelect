# MediaSelect
#####a library for select and record photo,audio,video.


----------

> ###简介

######一行代码完成 调用系统相册 和 视频，语音库，选择图片，视频，和音频文件。在选择界面实现了录制视频和录制音频功能。


> ###截图


![](https://github.com/hyr0318/MediaSelect/blob/master/gif/gif.gif)

----------
> ###如何使用

*	在build.gradle 中添加：


    `compile 'com.huangyirui:mediaselect_library:1.0.0'`


*	在需要调用的地方：


	```  MediaSelectActivity.openActivity(this, MediaType.PHOTO_SELECT_TYPE, 1000, mediaList,
            Constans.REQUEST_CODE);``` 


	*	第一个参数：传入Context
	*	第二个参数：传入的是选择类型 有三个类型  `MediaType.AUDIO_SELECT_TYPE` ：音频类型 `MediaType.PHOTO_SELECT_TYPE` ：图片类型 `MediaType.VIDEO_SELECT_TYPE` ：视频类型
	*	第三个参数：传入显示最大的文件数
	*	第四个参数：返回的数据集  类型为：`List<Photo> mediaList `
	*	第五个参数：`onActivityResult`返回码 


*	在返回的界面重写`onActivityResult` 方法


~~~   

	 @Override protected void onActivityResult(int requestCode, int resultCode, Intent data) {

        if (requestCode == Constans.REQUEST_CODE) {
            if (null != data) {
                mediaList =  data.getParcelableArrayListExtra(Constans.RESULT_LIST);

                mediaAdapter.setMediaList(mediaList);

                mediaAdapter.notifyDataSetChanged();
            }

        }
        super.onActivityResult(requestCode, resultCode, data);
    	}
	}
