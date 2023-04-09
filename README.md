# aaa

'use strict';

const romanMap = {
  'あ': ['a'], 'い': ['i', 'yi'], 'う': ['u', 'wu'], 'え': ['e'], 'お': ['o'],
  'か': ['ka', 'ca'], 'き': ['ki'], 'く': ['ku', 'cu', 'qu'], 'け': ['ke'], 'こ': ['ko', 'co'],
  'さ': ['sa'], 'し': ['si', 'shi', 'ci'], 'す': ['su'], 'せ': ['se', 'ce'], 'そ': ['so'],
  'た': ['ta'], 'ち': ['ti', 'chi'], 'つ': ['tu', 'tsu'], 'て': ['te'], 'と': ['to'],
  'な': ['na'], 'に': ['ni'], 'ぬ': ['nu'], 'ね': ['ne'], 'の': ['no'],
  'は': ['ha'], 'ひ': ['hi'], 'ふ': ['fu', 'hu'], 'へ': ['he'], 'ほ': ['ho'],
  'ま': ['ma'], 'み': ['mi'], 'む': ['mu'], 'め': ['me'], 'も': ['mo'],
  'や': ['ya'], 'ゆ': ['yu'], 'よ': ['yo'],
  'ら': ['ra'], 'り': ['ri'], 'る': ['ru'], 'れ': ['re'], 'ろ': ['ro'],
  'わ': ['wa'], 'ゐ': ['wyi'], 'ゑ': ['wye'], 'を': ['wo'], 'ん': ['nn', 'xn', 'n'],
  'が': ['ga'], 'ぎ': ['gi'], 'ぐ': ['gu'], 'げ': ['ge'], 'ご': ['go'],
  'ざ': ['za'], 'じ': ['ji', 'zi'], 'ず': ['zu'], 'ぜ': ['ze'], 'ぞ': ['zo'],
  'だ': ['da'], 'ぢ': ['di'], 'づ': ['du'], 'で': ['de'], 'ど': ['do'],
  'ば': ['ba'], 'び': ['bi'], 'ぶ': ['bu'], 'べ': ['be'], 'ぼ': ['bo'],
  'ぱ': ['pa'], 'ぴ': ['pi'], 'ぷ': ['pu'], 'ぺ': ['pe'], 'ぽ': ['po'],
  'うぁ': ['wha'], 'うぃ': ['whi'], 'うぇ': ['whe'], 'うぉ': ['who'],
  'きゃ': ['kya'], 'きぃ': ['kyi'], 'きゅ': ['kyu'], 'きぇ': ['kye'], 'きょ': ['kyo'],
  'くぁ': ['qa', 'qwa'], 'くぃ': ['qi', 'qwi'], 'くぇ': ['qe', 'qwe'], 'くぉ': ['qo', 'qwo'], 'くゃ': ['qya'], 'くゅ': ['qyu'], 'くょ': ['qyo'],
  'しゃ': ['sya', 'sha'], 'しぃ': ['syi'], 'しゅ': ['syu', 'shu'], 'しぇ': ['sye', 'she'], 'しょ': ['syo', 'sho'],
  'つぁ': ['tsa'], 'つぃ': ['tsi'], 'つぇ': ['tse'], 'つぉ': ['tso'],
  'ちゃ': ['tya', 'cha'], 'ちぃ': ['tyi'], 'ちゅ': ['tyu', 'chu'], 'ちぇ': ['tye', 'che'], 'ちょ': ['tyo', 'cho'],
  'てゃ': ['tha'], 'てぃ': ['thi'], 'てゅ': ['thu'], 'てぇ': ['the'], 'てょ': ['tho'],
  'とぁ': ['twa'], 'とぃ': ['twi'], 'とぅ': ['twu'], 'とぇ': ['twe'], 'とぉ': ['two'],
  'ひゃ': ['hya'], 'ひぃ': ['hyi'], 'ひゅ': ['hyu'], 'ひぇ': ['hye'], 'ひょ': ['hyo'],
  'ふぁ': ['fa'], 'ふぃ': ['fi'], 'ふぇ': ['fe'], 'ふぉ': ['fo'],
  'にゃ': ['nya'], 'にぃ': ['nyi'], 'にゅ': ['nyu'], 'にぇ': ['nye'], 'にょ': ['nyo'],
  'みゃ': ['mya'], 'みぃ': ['myi'], 'みゅ': ['myu'], 'みぇ': ['mye'], 'みょ': ['myo'],
  'りゃ': ['rya'], 'りぃ': ['ryi'], 'りゅ': ['ryu'], 'りぇ': ['rye'], 'りょ': ['ryo'],
  'ヴぁ': ['va'], 'ヴぃ': ['vi'], 'ヴ': ['vu'], 'ヴぇ': ['ve'], 'ヴぉ': ['vo'],
  'ぎゃ': ['gya'], 'ぎぃ': ['gyi'], 'ぎゅ': ['gyu'], 'ぎぇ': ['gye'], 'ぎょ': ['gyo'],
  'ぐぁ': ['gwa'], 'ぐぃ': ['gwi'], 'ぐぅ': ['gwu'], 'ぐぇ': ['gwe'], 'ぐぉ': ['gwo'],
  'じゃ': ['ja', 'zya'], 'じぃ': ['jyi', 'zyi'], 'じゅ': ['ju', 'zyu'], 'じぇ': ['je', 'zye'], 'じょ': ['jo', 'zyo'],
  'でゃ': ['dha'], 'でぃ': ['dhi'], 'でゅ': ['dhu'], 'でぇ': ['dhe'], 'でょ': ['dho'],
  'ぢゃ': ['dya'], 'ぢぃ': ['dyi'], 'ぢゅ': ['dyu'], 'ぢぇ': ['dye'], 'ぢょ': ['dyo'],
  'びゃ': ['bya'], 'びぃ': ['byi'], 'びゅ': ['byu'], 'びぇ': ['bye'], 'びょ': ['byo'],
  'ぴゃ': ['pya'], 'ぴぃ': ['pyi'], 'ぴゅ': ['pyu'], 'ぴぇ': ['pye'], 'ぴょ': ['pyo'],
   'ぁ': ['la', 'xa'], 'ぃ': ['li', 'xi'], 'ぅ': ['lu', 'xu'], 'ぇ': ['le', 'xe'], 'ぉ': ['lo', 'xo'],
    'ゃ': [], 'ゅ': [], 'ょ': [], 'っ': [],
  'ー': ['-'], ',': [','], '.': ['.'], '、': [','], '。': ['.'],
  '・': ['/'], '&#12289;': [','], '&#12290;': ['.'], '&#12539;': ['/']
};

const E_words = [
  'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N',
  'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z'];

let output = document.getElementById('output');
let text = document.getElementById('text');
let greeting = [];
let voice = [];
let keys = Object.keys(romanMap);
let vals = Object.values(romanMap);
let output_array = [];
const get = document.querySelectorAll('span');
let quiz = document.getElementById('quiz');
let kanaArray = Object.keys(romanMap);
let kanaRoma = Object.values(romanMap);

let children_text = document.querySelectorAll('#tap');
let virtual_keyboard = document.getElementById('virtual-keyboard');
let header = document.getElementById('header');
const timer = document.getElementById('time');
let startTime;
let originTime = 10;
let countCorrect = 0;
let keyboard = document.querySelector('.keyboard');
let countMiss = 0;
let count = 0;
let conta = document.getElementById('container');


let q;
for (let i = 0; i < obj.length; i++) {
  q = Object.values(obj[i]);
  greeting.push(q[2]);
  voice.push(q[3]);
  //  console.log(q[2]);
  //  console.log(q[3]);
};
// console.log(q);
//  let djoin = d.join("");
//  console.log(djoin);
//ただの変数宣言ではなく、空の文字列を用意しておくことで
//文字列を結合していくときに、最初にundefinedが入らない

document.addEventListener('keydown', logKey);
let d;

let all_Cho = [];

let cho_split1 = [];
let cho_split2 = [];
 let cho_split3 = [];


function split() {

  while (output.firstChild) {
    output.removeChild(output.firstChild);
  }

  while (text.firstChild) {
    text.removeChild(text.firstChild);
  }

  let random = Math.floor(Math.random() * voice.length);
  let sp = voice.splice(random, 1)[0];
  // console.log(sp);
  let spg = greeting.splice(random, 1)[0];
  quiz.innerText = spg;
  //Q
  quiz.insertAdjacentHTML('afterbegin', '<span>Q:</span>');

  let word = sp.split("");
  // console.log(word);
  for(let i=0;i<+word.length;i++){
    if(word.indexOf('ゃ')>0){
      let smallYa = word.indexOf('ゃ');
      let gattaiYa = word[smallYa-1]+word[smallYa];
      word.splice(smallYa,1);
      word.splice(smallYa-1,0);
      word[smallYa-1] = gattaiYa;
    };
     if(word.indexOf('ゅ')>0){
      let smallYu = word.indexOf('ゅ');
     let gattaiYu = word[smallYu-1]+word[smallYu];
     word.splice(smallYu,1);
     word.splice(smallYu-1,0);
     word[smallYu-1] = gattaiYu;
    };
     if(word.indexOf('ょ')>0){
      let smallYo = word.indexOf('ょ');
      smallYo;
      let gattaiYo = word[smallYo-1]+word[smallYo];
      word.splice(smallYo,1);
      word.splice(smallYo-1,0);
      word[smallYo-1] = gattaiYo;
    };
  }

  //  console.log(word);
  let chokin = "";
  for (let i = 0; i < word.length; i++) {
    let create = document.createElement('span');
    create.innerText = word[i];
    text.appendChild(create);
  }
  text.insertAdjacentHTML('afterbegin', '<span>A:</span>');

   let cho_split;
  let plus = 0;
  let tu;
  // console.log(word);

  word.forEach((one) => {
    // console.log(romanMap[one]);
    // console.log(romanMap[one][0]);
    // console.log(chokin2);
    if(plus === 1){
      let tu = romanMap[one][0].split('');
      // console.log(tu[0]);
      let tutu=[];
      tutu.push(tu[0]);
      all_Cho.push(tutu);
      chokin += tu[0];
      cho_split1.push(tu[0]);
      cho_split2.push(tu[0]);
      cho_split3.push(tu[0]);
       plus = 0;
    }

     if(romanMap[one].length === 0){
        plus++;
        return;
     };

    chokin += romanMap[one][0];
    
    all_Cho.push(romanMap[one]);
    cho_split1.push(romanMap[one][0]);

     if(romanMap[one].length > 1){
      cho_split2.push(romanMap[one][1]);
      // console.log(romanMap[one][1]);
     }else{
       cho_split2.push(romanMap[one][0]);
      //  console.log(romanMap[one][0]);
     }

     if(romanMap[one].length > 2){
      cho_split3.push(romanMap[one][2]);
      // console.log(romanMap[one][2]);
     }else{
       cho_split3.push(romanMap[one][0]);
      //  console.log(romanMap[one][0]);
     }

    //  console.log(chokin2);
    cho_split = chokin.split("");
  });

  //  console.log(cho_split);

  
  //  console.log(all_Cho);

  for (let i = 0; i < cho_split.length; i++) {
    let write = document.createElement('span');
   write.classList.add(i);
    write.innerText = cho_split[i].toUpperCase();
    output_array.push(cho_split[i]);
    output.appendChild(write);
  }

  d = document.querySelectorAll('#output span');
  d = Array.from(d);
  // console.log(d);
  StartTimer();
}
split();





let d_text = "";
// console.log(d_text);
let d_split;
let num = 0;

function dloop() {
   for (let i = 0; i < d.length; i++) {
     d_text += d[i].textContent;
     if (i === d.length - 1) {
       d_split = d_text.split("");
      
        // console.log(d_split.length);
       count += d_split.length;

       console.log(d_text);
       console.log(d_split);

     }
   }

   //とっておきたいやつ
  //   for (let i = 0; i < cho_split1.length; i++) {
  //   d_text += d[i].textContent;
  //   if (i === d.length - 1) {
  //     d_split = d_text.split("");
  //      console.log(d_text);
  //     console.log(d_split);
  //     console.log(d_split.length);
  //     count += d_split.length;
  //     console.log(d_split);
  //     console.log(d_text);
  //   }
  // }
  orange();
}
dloop();



let chocho = 0;
let v = 0;

let eee = '';




function logKey(e) {
  let gg = e.key.toUpperCase();
let under =document.getElementsByClassName('underLine')[0];


eee += e.key;
console.log(eee);
let c1 ='';
let c2 ='';
let c3 ='';
let underNext;
let underNextNext;
let kazoeru;
let span;


if(e.key !== cho_split1[0].charAt(0) && e.key === cho_split2[0].charAt(0) || e.key === cho_split3[0].charAt(0)){
  cho_split1.forEach((a)=>{
    for (let i = 0; i <= cho_split1.length; i++) {
          c1 += a.charAt(i);
    }
  })
  console.log(c1);
  
  cho_split2.forEach((a)=>{
    for (let i = 0; i <= cho_split2.length; i++) {
          c2 += a.charAt(i);
  
          if(eee === c2 && eee !== c1.charAt(i) && eee !== c3.charAt(i)){
            kazoeru = a.length;  
          //とっておきたいやつ
          //   if(cho_split1[i].length < kazoeru){
          //     span = document.createElement('span');
          //    span.classList.add('added');
          //    under.textContent = span;
          //    console.log(under);
          // }
        
            under.textContent = a.charAt(i).toUpperCase();
            d_split[1] = a.charAt(i).toUpperCase();
            d_split.shift();
            console.log(a.charAt(i).toUpperCase());
  
            console.log(d);
             let d_Array_Num = d.indexOf(under);
             console.log(d[d_Array_Num]);
              // d.splice(d_Array_Num,1,span)
              console.log(d);
              console.log(d_split);
            if(2<=kazoeru){
              // underNext = getElementsByClassName('added')[0];
              //  d_split.unshift(a.charAt(i+1).toUpperCase());
              d_split[0] = a.charAt(i).toUpperCase();
              // console.log(a.charAt(i+1).toUpperCase());
              let spa_Cre = document.createElement('span');
              spa_Cre.classList.add('added');
              spa_Cre.textContent = a.charAt(i+1).toUpperCase();
              // span.textContent = a.charAt(i+1).toUpperCase();
              under.after(spa_Cre);
              console.log('dekita?');
           }
  
          //  d_split.unshift(a.charAt(i).toUpperCase());
        
           
  
           
          //  if(3===kazoeru){
          //    underNextNext = span.nextElementSibling;
          //    underNextNext.textContent = a.charAt(i+2).toUpperCase();
          //    console.log(underNext);
          //    console.log('iketa?');
          //  }
          };
    };
  })
  
  
  cho_split3.forEach((a)=>{
    for (let i = 0; i <= cho_split3.length; i++) {
      c3+= a.charAt(i);
  
      if(eee === c3 && eee !== c1.charAt(i) && eee !== c2.charAt(i)){
         kazoeru = a.length;
          under.textContent = a.charAt(i).toUpperCase();
         if(2<=kazoeru){
             underNext = under.nextElementSibling;
             underNext.textContent = a.charAt(i+1).toUpperCase();
          }
          
          if(3<=kazoeru){
            underNextNext = underNext.nextElementSibling;
            underNextNext.textContent = a.charAt(i+2).toUpperCase();
          }
      }}
    });
}


      // for(let v=0; v<=a.length;v++){
      //   let c3Array =a.split('');
      //  let span = document.createElement('span');
      //        span.appendChild(c3Array[v]);
      //        if(v===0){
      //        }
         
      // }


      if(eee === cho_split1[0] || eee === cho_split2[0] || eee === cho_split3[0]){
        cho_split1.shift();
        cho_split2.shift();
        cho_split3.shift();
           
        eee = '';
      }


             

  if (d_split[0] !== gg) {
    //間違えた時に一瞬だけ光って色をheader部分に入れる方にする
    header.classList.add('highlight');
    // console.log('miss');
    countMiss++;

    setTimeout(() => {
      header.classList.remove('highlight');
    }, 50);
  }
  if (d_split[0] === gg) {
    //  console.log(d_split[0]);
   
    d[num].style.color = 'orange';
    num++;
    d_split.splice(0, 1);


    // console.log(d_split);
    if (d_split.length === 0) {
      if (voice.length === 0) {
        // 渡したいデータ
        let score = document.querySelector('[name="score"]');
        let miss = document.querySelector('[name="miss"]');
        let rate = document.querySelector('[name="rate"]');
        let level = document.querySelector('[name="level"]');

        let thr = document.getElementById('thr');

        score.value = count - countMiss;
        miss.value = countMiss;

        rate.value = Math.floor((count - countMiss) / count * 100);

        if (rate.value === 100) {
          level.value = 'SS';
        } else if (rate.value >= 90) {
          level.value = 'S';
        } else if (rate.value >= 80) {
          level.value = 'A';
        } else if (rate.value >= 70) {
          level.value = 'B';
        } else if (rate.value >= 60) {
          level.value = 'C';
        } else if (rate.value < 60) {
          level.value = 'D';
        }
        thr.submit();
        thr.stopPropagation();
      }

      d_text = "";
      split();
      dloop();
      num = 0;
    }
  }
  orange();
  underLine();
}


function orange() {
  children_text.forEach((value) => {
    if (value.classList.contains('keydown')) {
      value.classList.remove('keydown');
    }
    // console.log(value.textContent);
    if (d_split[0] === value.textContent) {
      // console.log('aa');
      value.classList.add('keydown');
    }

  })

}



//下線をつけるよ
function underLine() {
  if (d[num - 1]) {
    if (d[num - 1].classList.contains('underLine')) {
      // console.log(d[num-1]);
      d[num - 1].classList.remove('underLine');
    }
  }
  if (d[num]) {
    // console.log(d[num]);
    d[num].classList.add('underLine');
  }
}
underLine();

//タイマー


 function StartTimer() {
   timer.innerText = originTime;
   startTime = new Date();
   setInterval(() => {
     timer.innerText = originTime - getTimerTime();
     if (timer.innerText <= 0) {
       timer.innerHTML = 0;
       if (voice.length === 0) {
         // 渡したいデータ
         let score = document.querySelector('[name="score"]');
         let miss = document.querySelector('[name="miss"]');
         let rate = document.querySelector('[name="rate"]');
         let level = document.querySelector('[name="level"]');

         let thr = document.getElementById('thr');

         if (d_split.length > 0) {
           countMiss += d_split.length;
          //  console.log(countMiss);
         }

         if (countMiss > count) {
           countMiss = count;
          //  console.log(countMiss);
         }

         score.value = count - countMiss;
         miss.value = countMiss;

         rate.value = Math.floor((count - countMiss) / count * 100);

         if (rate.value === 100) {
           level.value = 'SS';
         } else if (rate.value >= 90) {
           level.value = 'S';
         } else if (rate.value >= 80) {
           level.value = 'A';
         } else if (rate.value >= 70) {
           level.value = 'B';
         } else if (rate.value >= 60) {
           level.value = 'C';
         } else if (rate.value < 60) {
           level.value = 'D';
         }
        thr.submit();
         thr.stopPropagation();

       }
       if (d_split.length >= 0) {
         countMiss += d_split.length;
         console.log(countMiss);
       }
       d_text = "";
       split();
       dloop();
       num = 0;
       underLine();
     }
   }, 1000)

 }

  //  function getTimerTime() {
    //  return Math.floor((new Date() - startTime) / 1000);
  //  }



// console.log(obj[i]);















  // let a = [];
   
  // let out ='';
  // let vvv=[];
  // console.log(all_Cho[0]);


  // all_Cho[0].forEach((o)=>{

            //   if(o.charAt(0) === e.key){
            //     vvv.push(o.replace(e.key,''));
            //     // console.log(all_Cho[0]);
            //   }else{
            //     vvv.push(o);
            //   }
            //  });

            // console.log(vvv);

      
            //   all_Cho[0].length = 0;
            //   // console.log(all_Cho[0]);
            //   vvv.forEach((o)=>{
            //   all_Cho[0].push(o);
            //   console.log(all_Cho[0]);            
            //  });

           

            //  all_Cho[0].forEach((h)=>{
            //    if(h ===''){
            //      all_Cho.shift();       
            //      console.log(all_Cho);                  
            //    }
            //  });
          
            //  console.log(all_Cho[chocho]);









