---
layout: post
title : NodeJS 기초9
categories: NodeJS
tags: [NodeJs,JavaScript]
---

**promise**

비동기 방식 함수는 콜백 함수가 필연적이다.  
(정상이면 어떻게 할지, 비정상이면 어떻게 할지를 처리를 위해)   
그렇지만 안타깝게도 비즈니스 로직을 만들다 보면 한가지 기능만을 가진 함수만 만들게 아니라   

여러가지의 작업이 한번에 이뤄지는 함수도 만들어야 한다.   
이런 경우 콜백이 계속 이뤄지는 이른바 콜백지옥이 나타나게 된다.  

그래서 es6에 도입된 문법이 있는데 그것이 바로 promise이다   

[//]: <> (비동기 작업 IF + catch )

    const condition = true;
    const promise = new Promise((resolve, reject) => {
        if(condition) {
            resolve('성공')
        } else {
            reject('실패')
        }
    });

    promise
        .then((message) => {
           return message 
           // then에서 return은 다음 then 아규먼트로 바인드 된다.
        })
        .then((message) => {
            console.log(message) 
            // 성공(resolve)
        })
        .catch((error) => {
            console.error(error) 
            // 실패(reject)
        });


콜백이 계속 되며 깊어지는 문법에 비해서 promise는 가독성이 훨신 더 좋아진걸 알수 있다.


[//]: <> (
    ECMA2017에 추가된 문법이다. 
    async는 프로미스 기반이며 프로미스 가독성을 좋아진 느낌이다.
    await는 async가 붙어진 내부에서만 사용 가능하다
    async func<> => { 
        try {
        const user = await Users.findOne<'zero'>;
        const updateUser = await Users.update<'zero', 'nero'>;
        const removeUser = await Users.remove<'zero', 'nero'>;
        console.log<'다 찾았니'>;
        } catch <err> {
            console.err<err>
        }    
    }
    func<>
)



