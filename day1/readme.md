기본
===
React를 시작하기 위해 관련 파일의 링크를 걸어준다.

```
<script crossorigin src="https://unpkg.com/react@16.13.1/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16.13.1/umd/react-dom.development.js"></script>
```

Babel을 사용하기 위해 링크를 걸어준다. 최신화된 스크립트를 브라우저에서 인식할 수 있도록 해준다.
```
<script src = "https://unpkg.com/babel-standalone@6.26.0/babel.min.js"></script>
```


```
        <div id="root"> </div>
        <script type="text/babel">
            const e = React.createElement;
            //객체 생성(재사용가능 한 컴포넌트)
            class LikeButton extends React.Component{
                //생성자
                constructor(props){
                    super(props);
                    //상태값(변하는 값)
                    this.state = {
                        liked : false,
                    }
                }
                //화면에 그려줄 부분
                render(){
                    return <button type='submit' onClick={() => {this.setState({liked:!this.state.liked})}}>                    
                        {this.state.liked ? 'liked' : 'like'}
                    </button>;
                }
            }


        </script>
        <script type="text/babel">
            //컴포넌트를 렌더링 한다. id 가 root인 곳에
            ReactDOM.render(<LikeButton />, document.querySelector('#root'));
        </script>
```

클래스에 메서드만들기

```
       class Gugudan extends React.Component {
            constructor(props) {
                ...
            }

            //아래는 클래스 내에서 this.메서드명 으로 호출된다.
            calc = (e) => {
                ...
            }

            change = (e) =>{
                this.setState({value:e.target.value})
            }
              
            render() {
                return (
                    ...
                        //함수를 호출하는 부분이다. { this.calc}
                        <button onClick={this.calc}>입력!</button>
                        ...
                    );
            }
        }
```

render시 div tag 제거하기
===
지금 우선은 React.Fragment로 변경한다.

constructor
===
```
//constructor 없이 아래처럼 바로 써도 된다.
class Gugudan extends React.Component {
            state = {
                    first : Math.ceil(Math.random() * 9),
                    second : Math.ceil(Math.random() * 9),
                    value : '',
                    result : ''
                }
            
```

함수형 setState
===
```
//현재 state값을 변경시키기 위해 this.state.first를 사용하지만 setState는 비동기로 작동한다. 그래서 함수형으로 변경한 후 명시적으로 이전값을 사용하도록 한다.
this.setState({    
    first : this.state.first
});
//함수형으로 변경한 setState
this.setState((prevState) =>{                
    return {    
        first : prevState.first    
    };                 
});
```