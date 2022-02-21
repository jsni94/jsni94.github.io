# 2022-02-21_TIL_useState의 활용

# ✍️Learn

- 직관적이고 간단한 useState의 활용법에 대해 학습할 수 있었다
    
    
    (사용예시)
    
    - **기본적인 useState 사용법**
    
    ```jsx
    
    const [content, setContent] = useState("");
    const [author, setAuthor] = useState("");
    
    ```
    
    만약 하나의 컴포넌트 안에 사용해야 할 state가 많다면 아래와 같이 코드를 짤 수 있다.
    
    - **useState의 응용법**
    
    ```jsx
    const [state, setState] = useState({
        author: "",
        content: "",
      });
    ```
    
    위처럼 객체의 형식으로 각각의 initialstate를 할당하고 사용할 수 있는데 state가 많아지면 많아질수록 useState의 응용법이 더욱 유용해진다.
    

# ❗주의할점

- useState응용법을 사용하게 될 때 setState를 활용하려면 반드시 객체의 형태로 사용해주어야 한다. 객체의 형태로 사용하지 않고 원래의 방식대로 setState를 사용하게 되면 객체안의 모든 initialstate를 변경해주기 때문이다.

(예시 _ author state를 변경해주고자 할 때)

```jsx
<input onChange={(e)=>{setState({
		author: e.target.value,
    content: state.content,
})}}/>
```

위처럼 코드를 짜게 되면 author의 값으론 onChange event객체의 value값이 content엔 initialstate가 남게 되어 원하는 state의 값만 변경해줄 수 있다.

아래처럼 태그에 name속성을 부여해  함수를 통해 더 직관적으로 코드 작성도 가능하다.

```jsx
const handleChangeState = (e) => {
    console.log(e.target.name);
    console.log(e.target.value);

    setState({
      [e.target.name]: e.target.value,
    });
  };

<input
          name="author"
          value={state.author}
          onChange={handleChangeState}
        />
```

# 🤷정리

- 객체를 활용해 useState 코드를 더욱 직관적이고 간편하게 작성할 수 있다.
- 객체를 활용해 useState를 이용할 때 state를 변경해 주려면 반드시 똑같은 객체 형태로 반환해 주어야 불필요한 state값의 변경을 막을 수 있다.