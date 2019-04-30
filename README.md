A reusable responsive react.js tab component with dynamic contents.

## NPM Package
https://www.npmjs.com/package/react-reusable-tabs

## Demo
https://reusable-table-component.firebaseapp.com/machines/59d9f4b4-018f-43d8-92d0-c51de7d987e5#/

## Usage
### Use react-reusable-tabs as below.

## import React from 'react'

## import { Tab } from 'react-reusable-tabs'


## const App = () => (
    
## <Tab
	tabTitle="Machine Details"
  	tabDescription="This tab for machine details"
  	tabLinks={getMachineTabs()}
 	selectedTab={this.state.selectedTab}
  	clickTab={this.clickTabHandler}
  	details={this.getDetail}
  	events={this.getEvents}
  	liveEvents={this.getLiveEvents}
	 />
## );
	    

	
// initiate default tab

## state = {

  selectedTab: 'details'
  
## }

// handle selected tab

## clickTabHandler = (tabName) => {

	this.setState({
	
      ...this.state,
      
      selectedTab: tabName
      
   });
   
## }

// initiate tabs

## export const getMachineTabs = () => {

    return [
        { label: 'Details', name: 'details' },
        { label: 'Events', name: 'events' },
        { label: 'Live Events', name: 'liveEvents' }
    ]
    
## }

// prepare machine details

## getDetail = () => {
        if (!this.props.machine) return 'No record found.';

        const labels = Object.keys(this.props.machine);
        const details = labels.map((l, i) => {
            let detail = '';
            if (l !== 'events') {
                detail = <div key={i}><strong>{startCase(toLower(replace(l, /_/g, ' ')))}</strong>: {this.props.machine[l]}</div>
            }
            return detail;
        })

        return details.length > 0 ? details : 'No record found.';
   ## }

// prepare events for machine
    
## getEvents = () => {
        if (!this.props.machine) return 'No record found.';

        const details = this.props.machine.events.map((e, i) => {
            const labels = Object.keys(e);
            const events = labels.map((l, i) => (
                <div key={i}><strong>{startCase(toLower(l))}</strong>: {e[l]}</div>
            ))
            return events
        });

        return details.length > 0 ? details : 'No record found.';
   ## }

 // prepare live events for machine
    
 ## getLiveEvents = () => {
        if (!this.props.liveEvents) return 'No record found.';

        const details = this.props.liveEvents.filter(lv => lv.machine_id === this.props.machine.id).map((e, i) => {
            const labels = Object.keys(e);
            const events = labels.map((l, i) => (
                <div key={i}><strong>{startCase(toLower(l))}</strong>: {e[l]}</div>
            ))
            return events
        });

        return details.length > 0 ? details : 'No record found.';
   ## }
    
// sample records
## {
	
{
			"status": "running",
			"machine_type": "microscope",
			"longitude": 48.09540056785246,
			"latitude": 11.523880271993598,
			"last_maintenance": "2017-04-01T15:00:00.000000Z",
			"install_date": "2015-04-18",
			"id": "68015cc1-3119-42d2-9d4e-3e824723fe03",
			"floor": 5
		}
## }

## Notes

‘name’ property of method getMachineTabs should match the the props name of Tab component. In the example above of this method there are several values for name property like 'details' 'events' 'liveEvents'. So these same named values also defined as props of Tabs which works as reference functions to return content for each tab content. Please check above examples to understand better.

## Installation

## npm

## npm i react-reusable-tabs --save

## yarn

## yarn add react-reusable-tabs 
 
 
 


