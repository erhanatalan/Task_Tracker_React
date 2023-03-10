<!-- # <center>ð [NBA Legends Project](https://nba-legends-with-react.netlify.app/) ð</center>
â
<hr>
â
## <center>ð PROJECT STEPS ð</center>
â
<hr>
â
## â¨ï¸ Install Bootstrap ï¿½ï¿½
â
```bash
npm install react-bootstrap bootstrap
```
â
<hr>
â
## ï¿½ï¿½ Import CSS ï¿½ï¿½ The following line can be included in your src/index.js or App.js file ï¿½ï¿½
â
```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```
â
<hr>
â
## ï¿½ï¿½ Index.css ï¿½ï¿½
â
```css
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-image: url("./assets/lebron-james-lakers-mixed-media-elite-editions.jpg");
  background-repeat: no-repeat;
  background-size: 100%;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
```
â
<hr>
â
## ï¿½ï¿½ Create "components" folder under "src" folder
â
<hr>
â
## ï¿½ï¿½ Create "Header.jsx" file under "components" folder ï¿½ï¿½
â
```javascript
import { Container, Image } from "react-bootstrap"
import nbaLogo from "../assets/nba-logo.png"
â
const Header = () => {
  return (
    <Container className="text-center mt-4">
        <Image src={nbaLogo} width="200px"></Image>
        <h1 className="my-2 font-monospace display-4">NBAðLegends</h1>
    </Container>
  )
}
â
export default Header
```
â
<hr>
â
## ï¿½ï¿½ Create "CardContainer.jsx" file under "components" folder ï¿½ï¿½
â
```javascript
import { Col, Container, Row, Form } from "react-bootstrap"
//! ð Since data is exported as "export const", we need to call it in curly braces while importing.
import { data } from "../helpers/data"
import PlayerCards from "./PlayerCards"
import { useState } from "react";
â
const CardContainer = () => {
    const [search, setSearch] = useState("");
    return (
        <>
            <Form.Control
                type="search"
                placeholder="Search Player..."
                className="w-50 m-auto"
                onChange={(e) => setSearch(e.target.value)}
            />
            <Container className="card-container rounded-4 my-4 p-3">
                <Row className="gap-3 justify-content-center">
                    {data.filter((player) => player.name.toLowerCase().includes(search.trim().toLowerCase())).map((player, index) => (
                        <Col md={6} lg={4} xl={3} key={index}>
                            <PlayerCards {...player} />
                        </Col>
                    ))}
                </Row>
            </Container>
        </>
    )
}
â
export default CardContainer
```
â
<hr>
â
## ï¿½ï¿½ Add styling to "index.css" for CardContainer ï¿½ï¿½
â
```css
/*! Player Card-Container Styling */
.card-container{
  background-image: url("https://p4.wallpaperbetter.com/wallpaper/661/973/110/cool-nba-logo-wallpaper-preview.jpg");
  min-width:300px;
}
```
â
<hr>
â
## ï¿½ï¿½ Create PlayerCards.jsx for rendering players under "components" folder ï¿½ï¿½
â
```javascript
import { useState } from "react";
import { Card } from "react-bootstrap";
â
const PlayerCards = ({ name, img, statistics }) => {
    //? ð const {name, image, statistics} = props
    const [showImage, setShowImage] = useState(true);
    const handleClick = () => setShowImage(!showImage);
    return (
        <Card
        //? onClick={() => setShowImage(!showImage)}
        onClick={handleClick}
        className="rounded-2 m-auto player-card" role="button">
            {showImage ? (
                <Card.Img variant="top" src={img} className="player-img" />
            ) :
                (
                    <ul className="m-auto">
                        {statistics.map((item, index) => {
                            return (
                                <li className="h5 text-start list-unstyled" key={index}>ð {item}</li>
                            )
                        })}
                    </ul>
                )}
            <Card.Footer>
                <Card.Title>{name}</Card.Title>
            </Card.Footer>
        </Card>
    );
};
â
export default PlayerCards;
```
â
<hr>
â
## ï¿½ï¿½ Add styling to "index.css" for PlayerCards ï¿½ï¿½
â
```css
/*! Player Card Styling */
.player-card{
  height:400px;
  max-width:280px;
  min-width:230px;
}
.player-card:hover{
  box-shadow: rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset, rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset, rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, rgba(0, 0, 0, 0.06) 0px 2px 1px, rgba(0, 0, 0, 0.09) 0px 4px 2px, rgba(0, 0, 0, 0.09) 0px 8px 4px, rgba(0, 0, 0, 0.09) 0px 16px 8px, rgba(0, 0, 0, 0.09) 0px 32px 16px;
}
â
.player-img{
  transition: transform 0.4s;
  height:350px;
}
â
.player-card:hover .player-img{
  transform:scale(0.95);
}
```
â
<hr>
â
# <center> ð© DEPLOYMENT ð© </center>
â
## ï¿½ï¿½ Deployment Notes
â
- There should be only one lock file "package-lock.json" or "yarn.lock".
- There shouldn't be any warnings in your application.
- If you have deployed your app to github pages before, you should remove "homepage" property from "package.json".
â
<hr>
â
## ï¿½ï¿½ For deployment; to create a "build" folder ï¿½ï¿½
â
```bash
yarn run build
```
â
<hr>
â
## ï¿½ï¿½ Go to [Netlify](https://www.netlify.com/) and deploy the site with "Import an existing project" option. -->
