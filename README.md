# React QUIZ APP

![image](https://github.com/user-attachments/assets/96473826-0a10-49a4-84a0-ddb7fc829af1)

# React Quiz App

The project is a simple quiz application built using React, where users can test their knowledge on a particular subject or topic. It displays a series of questions with multiple-choice options, provides feedback on correct or incorrect answers, and keeps track of the user's score. The application allows users to move on to the next question and displays the final score at the end. It also features a reset button to start the quiz over.


## Features in this project

- Score Correcting
- Answer Checking
- Question Index
- State Management
- Reset Feature
- Option Refs

## Function used

All the declearation that had to be made

```javascript
  let [index, setIndex] = useState(0);
  let [question, setQuestion] = useState(data[index]);
  let [lock, setLock] = useState(false);
  let [score, setScore] = useState(0)
  let [result, setResult] = useState(false)
```

Function for the checking answers

```javascript
  
  const checkAns = (e,ans) => {
    if (lock === false) {
      if (question.ans===ans) {
        e.target.classList.add("correct");
        setLock(true);
        setScore(prev=>prev+1);
      }
      else{
        e.target.classList.add("wrong")
        setLock(true);  
        option_array[question.ans-1].current.classList.add("correct")
      }
    }    
  }

```

This is to make the button move to the next question, and then removing the previous highlight of the wrong and correct answer

```javascript
  
    const next = ()=>{

    if(lock===true) {
      if (index === data.length-1) {
        setResult(true)
        return 0;
      }
      setIndex(++index);
      setQuestion(data[index]);
      setLock(false);
      option_array.map((option)=> {
        option.current.classList.remove("wrong");
        option.current.classList.remove("correct");
        return null
      })
    }

  }

```

The reset button only appears at th end of the quiz, it resets the question counter to Zero, the score to zero. and it then sets the screen lock and results to false. to prevents the old scores to still be displayed and enables the user to click for the next question.

```javascript
  
    const reset = () => {
    setIndex(0);
    setQuestion(data[0]);
    setScore(0);
    setLock(false);
    setResult(false);
  }

```


Heres is where all the pieace of code comes together!

```javascript
  return ( 
    <div className='container'>
      <h1>Quiz App</h1>
      <hr />
      {result?<></>:<>
      <h2>{index+1}.{question.question}</h2>
        <ul>
          <li ref={Option1} onClick={(e)=>{checkAns(e,1)}}>{question.option1}</li>
          <li ref={Option2} onClick={(e)=>{checkAns(e,2)}}>{question.option2}</li>
          <li ref={Option3} onClick={(e)=>{checkAns(e,3)}}>{question.option3}</li>
          <li ref={Option4} onClick={(e)=>{checkAns(e,4)}}>{question.option4}</li>
        </ul>
        <button onClick={next}>Next</button>
        <div className="index">{index+1} of {data.length} question</div></>}

        {result?<>
            <h2>You Score {score} out of {data.length}</h2>
        <button onClick={reset}>Reset</button>
        </>:<></>}
    </div>
  )
} 

export default Quiz
```


## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://osadeveloper-por.netlify.app/)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/osazemen-osawaru-odeh-005844291/)
[![youtube](https://img.shields.io/badge/youtube-ff4500?style=for-the-badge&logo=youtube&logoColor=red)](https://www.youtube.com/@OsazemenGmrYT)


## Support

For support, email osazemenod@gmail.com or follow me on linked : ).


## Related

Here is some of my other projects

[Music Player](https://github.com/Osalino/music-player)

[YouTube MP3 Converter](https://github.com/Osalino/youtube-mp3-conv)

[Simple Python Chatapp](https://github.com/Osalino/PythonnChat-App)







Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
