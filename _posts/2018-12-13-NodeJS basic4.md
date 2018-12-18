---
layout: post
title : NodeJS 기초4
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**path**   
경로 다루는 모듈   
경로 정규화   
경로 생성   
디렉토리/파일 이름 추출    
파일 확장자 추출   

전역객체 (global)   
- __filename   
- __dirname (같은 폴더)
  
**예제 code**   
같은 폴더 내 이미지 경로

    var path = __dirname+'/image.png';

**경로 다듬기 예제 code**

    pathUtil.normalize('/user/tmp/../local///bin/'); 경로 다듬기
    // returns
    
    result : /user/local/bin/  
    normalize로 경로를 다듬은 결과이다.

**경로 구성 요소 얻기**
 
    var path = '/foo/bar/baz/asdf/asdf.html';
    
    pathUtil.dirname(path)  파일이 포함된 폴더 경로  
    result : /foo/bar/baz/asdf
    pathUtil.basename(path) 파일 이름, 경로 중 마지막 요소  
    result : asdf.html
    pathUtil.extname(path) 확장자 추출 
    result : .html

    var info = path.parse('/home/user/dir/file.txt')
    {
        root:'/'
        dir:'home/user/dir'
        base:'file.txt'
        ext:'.txt'
        name:'file
    }
    // parse로도 가져온다 
    info.root 
    info.base  // 필요한것만 사용 가능하다

경로 다루기   
   
        경로 연산   
        path.Util.sep  (seperate)   
        __dirname + pathUtil.sep + 'image.png';  

        경로 붙이기   
        pathUtil.join('/foo','bar','baz/asdf','test.html')   
        result : '/foo/bar/baz/asdf'

        경로 만들기
        pathUtil.foramt()    
        var path = pathUtil.format ({   
            root:'/'   
            dir:'/home/user/dir'   
            base:'file.txt'   
            ext:'.txt'   
            name:'file   
        });
        result : 'home/user/dir/file.txt'
        
경로 알아내기    

        path.resolve('.');
        path.resolve('../', 'libs');

---

**fs**
 
 파일시스템모듈 : fs   
 var fs = require('fs'); // 준비 후 사용가능하다 

 주요 기능   
- 파일 생성/읽기/쓰기/삭제
- 파일 접근성/속성
- 디렉토리 생성/읽기/삭제
- 파일 스트림

**주의 : 모든 플랫폼에 100% 호환되지 않는다**

fs 모듈의 특징   
비동기와 동기 방식 함수 모두 사용 제공 한다   

비동기식   
- callback 사용
- 논-블럭 방식

       fs.readfile('textfile.txt', 'utf8', 
            function(error,data) {
        });

비동기식 예외처리   

        fs.readFile('extfile.txt', 'utf-8',function(err, data){
            // err 콜백함수로서 에러가 발생하면 err에 담기는것으로 예외처리 한다
            if(err) {
                console.error('Readfile error', err);
            } else {
                // 정상 처리
            }

        });

동기식 
- 이름규칙 : + Sync(readFileSync)
- 블록(block) 방식 - 성능상 주의
- 반환값이 이용   

        var data = fs.readFileSync('textfile.txt','utf8');

동기식 예외처리 

        try {
            var data = fs.readFileSync('textfile.txt','utf8');
        } catch (exception) {
            console.error('readFile error:', exception)
        }



파일 다루기   
- 파일 디스크립터 (파일 디스크립터란 시스템으로부터 할당받은 파일 또는 소켓에 부여된 정수를 의미한다)   
 <a href="https://m.blog.naver.com/PostView.nhn?blogId=yurhyur1&logNo=50122605420&proxyReferer=https%3A%2F%2Fwww.google.com%2F">참고 블로그</a>

 - 파일 경로로 파일 다루기   
    -  파일 종류  
        - 문자열 읽기 : 인코딩    
        - 바이너리 읽기 : buffer    

    
    Code

        fs.read(fd,buffer,offset,length,position,callback)
        fs.readySync(fd,buffer,offset,length,position)
        //fd를 지정한다

        // 아래와 같이 사용 가능하다

        // 파일 디스크립터 얻기
        vaf fd = fs.openSync(path,flags[, mode])
            fs.open(path,flags[,mode],function(err,fd){
        });

        // flags 
        // r(읽기), w(쓰기), a(추가)...

        fs.close(fd,callback)
        fs.closeSync(fd)
      
    파일읽기   
    동기방식 예제
     
        fs.readFile(filename[,option], calback)   
        fs.readFileSync(filename,[,option])
        // filename은 파일 경로
        
        // Exam
        var fd = fs.open(file,'r')
        // 파일경로 지정하고 읽기 모드로 파일을 읽는다. 
        var buffer = new Buffer(10)
        // buffer 크기를 10으로 만든다

        var byte = fs.readSync(fd, buffer, 0, buffer.length, 0);
        // 동기식으로 파일을 읽어 buffer에 담는다
        console.log('File.Content: ', buffer.toString('utf-8'));
        // buffer를 utf-8 문자열로 바꾼다음에 콘솔에 출력
        fs.closeSynce(fd)


    비동기방식 예제

        fs.open(file, 'r', function(err,fd2){
            var buffer2 = new buffer(20);
            fs.read(fd2, buffer2, 0, buffer2.length, 10, function(){
                console.log('File Read ', byteRead,'bytes');
                console.log('File Contents : ', buffer.toString('utf-8'));
                fs.close(fd, function(err){});
            });
        });

