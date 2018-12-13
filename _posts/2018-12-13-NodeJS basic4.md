---
layout: post
title : NodeJS 기초4
categories: NodeJS
tags: [NodeJs,JavaScript,기초,입문]
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
            // err 콜백함수로서 에러가 발생하면 err에 담긴다 
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




