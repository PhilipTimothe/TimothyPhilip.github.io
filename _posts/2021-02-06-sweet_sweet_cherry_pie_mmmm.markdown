---
layout: post
title:      "Sweet Sweet Cherry Pie! Mmmm"
date:       2021-02-06 19:22:55 +0000
permalink:  sweet_sweet_cherry_pie_mmmm
---


That React Bootstrap cherry pie!  I think I love it.  Even though the plan it to dive deeper into gaining more experience in CSS for personal use, I think Bootstrap has some of the greatest tools at anyones fingertips.  I must be honest, it is a bit daunting putting it all together the first time anyone tries but as anyone that is into coding knows, you only get better the more you code.  Yup that's what I did and I ended up with this as a component ...

```
import React, { useState } from 'react';
import CompanyChartContainer from '../containers/CompanyChartContainer'
import { Link } from "react-router-dom";
import { connect } from 'react-redux'
import { setPortfolio } from '../redux/actionCreator'
import Card from 'react-bootstrap/Card';
import Button from 'react-bootstrap/Button';
import Tabs from 'react-bootstrap/Tabs';
import Tab from 'react-bootstrap/Tab';

function CompanyOverview(props) {
    const [key, setKey] = useState('overview');
    
    return ( 
        <>
        <Tabs id={props.id} style={{ width: '50rem', margin: '1rem auto' }} unmountOnExit activeKey={key}
      onSelect={(k) => setKey(k)}>
            <Tab eventKey="overview" title="Company Overview">
                <Card style={{ width: '50rem', margin: '1rem auto' }} >
                    <Card.Body >
                        <Card.Title>{props.name}</Card.Title>
                        <Card.Text>
                            Company Symbol: {props.symbol} <br/>
                            Industry: {props.industry} <br/>
                            Asset Type: {props.assetType} <br/>
                            Currency: {props.currency} <br/>
                            exchange: {props.exchange} <br/>
                            Country: {props.country} <br/>
                            Sector: {props.sector} <br/>
                            Address: {props.address} <br/>
                            <br/>
                            Description: {props.description} <br/>
                        </Card.Text>
                            <Button variant="dark" onClick={() => props.setPortfolio(props.company)}> Add to Portfolio </Button>{' '}
                            <Link to="/">
                                <Button variant="dark" > Start a New Search </Button>{' '}
                            </Link>
                    </Card.Body>
                </Card>
            </Tab>
            <Tab eventKey="datachart" title="Data Chart">
                <Card style={{ width: '50rem', margin: '1rem auto' }} >
                    <Card.Body >
                        <Card.Title>{props.name}</Card.Title>
                        <Card.Text>
                            {<CompanyChartContainer id={props.param} />}
                        </Card.Text>
                    </Card.Body>
                </Card>
            </Tab>
        </Tabs>
        </>
    )
}

export default connect(null, {setPortfolio}) (CompanyOverview)
```

I took a bit of time but I got the hang of it.  

I will say, these tools are such a beautiful thing.  I never thought that some difficult parts of coding to actually be easier and close a nice summers walk.  It's definitely not a breeze but it levels you up.  At least it did for me!  I will say this, React and Boostrap has re-excited me to dive in more with all the different types of frameworks and middleware and etc.  And lastly, I owe a huge thanks to Flatiron School for opening the door to this new part of my life. " Keep coding " will me my mantra from now till I can't type anymore.  ! 
