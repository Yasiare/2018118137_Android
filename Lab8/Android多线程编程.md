# 子线程的程序框架

## 一、实验目的：探究Android的多线程编程

## 二、实验过程：

### 1、子线程框架主要代码：

#### 框架1

```java
public class MYThread extends Thread{

    @Override
    public void run(){
        //处理具体的逻辑
    }
}
```

#### 框架2

```java
class MYThread implements Runnable{

    @Override
    public void run(){
        //处理具体的逻辑
    }
    
    Mythread mythread = new MYThread();
    new Thread(mythread).start();
}
```

#### 框架3

```java
new Thread(new Runnable(){
    @Override
    public void run(){
        //处理具体的逻辑
    }
}).start();
```

### 2、消息处理机制和多线程之间的数据交换

#### 主要代码：

```java
class DownloadTask extends AsyncTask<Void, Integer, Boolean>{
    
    @Override
    protected void onPreExecute(){
		progressDialog.show(); //显示进度对话框
    }
    
    @Override
    protected Boolean doInBackground(Void... params){
		try{
            while(true){
                int downloadPercent = doDownload();//这是一个虚构的方法
                publishProgress(downloadPercent);
                if(downloadPercent >= 100){
                    break;
                }
            }
        } catch(Exception e){
            return false;
        }
        return true;
    }
    
    @Override
    protected void onProgressUpdate(Integer... values){
        //在这里更新下载进度
        progressDialog.setMessage("Downloaded" + values[0] + "%");
    }
    
    @Override
    protected void onPostExecute(Boolean result){
        progressDialog.dismiss(); //关闭进度对话框
        //在这里提示下载结果
        if(result){
            Toast.makeText(context, "Download succeeded", Toast.LENGTH_SHORT).show();
        } else{
            Toast.makeText(context, "Download failed", Toast.LENGTH_SHORT).show();
        }
    }
}
```

#### 启动方式：

```java
new DownloadTast().execute();
```



