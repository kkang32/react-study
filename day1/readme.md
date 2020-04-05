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