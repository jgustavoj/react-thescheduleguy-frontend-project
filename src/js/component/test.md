

Previous Register and Login pill


``` js
// const [logging, setLogging] = useState("");
// <div className="row justify-content-center no-gutters">
// 				<div className="col-lg-4" />
// 				<div className="col-lg-4">
// 					<div className="card">
// 						<div className="container-account">
// 							{/* <div className="account-tab"> */}
// 							<ul className="nav nav-pills mb-3 justify-content-center " id="pills-tab" role="tablist">
// 								<li className="nav-item">
// 									<button className="btn btn-light" onClick={() => setLogging("login")}>
// 										Login
// 									</button>
// 								</li>
// 								<li className="nav-item">
// 									<button className="btn btn-secondary" onClick={() => setLogging("register")}>
// 										Register
// 									</button>
// 								</li>
// 							</ul>
// 							<div className="tab-content" id="pills-tabContent">
// 								<div
// 									className="tab-pane fade show active"
// 									id="pills-home"
// 									role="tabpanel"
// 									aria-labelledby="pills-home-tab">
// 									{logging == "register" ? (
// 										<Register />
// 									) : (
// 										<form>
// 											<div className="form-group row">
// 												<div className="col">
// 													<input type="text" className="form-control" placeholder="Email" />
// 												</div>
// 											</div>
// 											<div className="form-group row">
// 												{/* <label htmlFor="inputPassword3" className="col-md-0 col-form-label" /> */}
// 												<div className="col-sm-10">
// 													<input
// 														type="password"
// 														className="form-control"
// 														id="inputPassword3"
// 														placeholder="Create Password"
// 													/>
// 												</div>
// 											</div>
// 											<Link to="/calendar">
// 												<button type="button" className="btn btn-secondary text-center mb-3">
// 													Sign In
// 												</button>
// 											</Link>
// 										</form>
// 									)}
// 								</div>
// 								{/* <div
// 							className="tab-pane fade"
// 							id="pills-profile"
// 							role="tabpanel"
// 							aria-labelledby="pills-profile-tab"
// 						/> */}
// 							</div>
// 							{/* </div> */}
// 						</div>
// 					</div>
// 				</div>
// 				<div className="col-lg-4" />
// 			</div>

//previous calendar view 

import React, { useState, useEffect } from "react";
import Paper from "@material-ui/core/Paper";
import { ViewState } from "@devexpress/dx-react-scheduler";
import {
	Scheduler,
	ViewSwitcher,
	DayView,
	WeekView,
	MonthView,
	Toolbar,
	DateNavigator,
	Appointments,
	TodayButton
} from "@devexpress/dx-react-scheduler-material-ui";
import "react-datepicker/dist/react-datepicker.css";

export const Calendar = () => {
	const currentDate = new Date();
	const [startDate, setStartDate] = useState(new Date());
	const [endDate, setEndDate] = useState(new Date());

	const [events, setEvents] = useState([
		{ startDate: "2020-11-12T09:45", title: "Meeting" },
		{ startDate: "2020-11-13T12:00", title: "Go to a gym" },
		{ startDate: "2020-11-14T13:00", title: "Groceries" },
		{ startDate: "2020-11-11T15:00", title: "Run" }
	]);

	// useEffect(() => {
	// 	fetch(
	// 		"https://3000-e602aabd-5ee2-4e3c-83ab-16569a08f1a5.ws-us02.gitpod.io/todos"
	// 	)
	// 		.then(function(response) {
	// 			if (!response.ok) {
	// 				throw Error(response.statusText);
	// 			}
	// 			// Read the response as json.
	// 			return response.json();
	// 		})
	// 		.then(function(responseAsJson) {
	// 			// Do stuff with the JSON
	// 			console.log("responseAsJson", responseAsJson);
	// 			setTodos(responseAsJson);
	// 		})
	// 		.catch(function(error) {
	// 			console.log("Looks like there was a problem: \n", error);
	// 		});
	// }, []);

	const handleChange = e => {
		setSingleEvent(e.target.value);
	};
	const handleClick = e => {
		const newEvent = {
			startDate: startDate,
			endDate: endDate,
			title: singleEvent
		};
		setEvents([...events, newEvent]);
		// 	fetch(
		// 		"https://3000-e602aabd-5ee2-4e3c-83ab-16569a08f1a5.ws-us02.gitpod.io/todos",
		// 		{
		// 			method: "POST",
		// 			body: JSON.stringify(singleTodo), // data can be `string` or {object}!
		// 			headers: {
		// 				"Content-Type": "application/json"
		// 			}
		// 		}
		// 	)
		// 		.then(res => res.json())
		// 		.then(response => setTodos(response))
		// 		.catch(error => console.error("Error", error));
		// 	setSingleTodo({ label: "" });
	};

	// const deleteTodo = id => {
	// 	fetch(
	// 		"https://3000-e602aabd-5ee2-4e3c-83ab-16569a08f1a5.ws-us02.gitpod.io/todos" +
	// 			"/" +
	// 			id,
	// 		{
	// 			method: "DELETE",
	// 			headers: {
	// 				"Content-Type": "application/json"
	// 			}
	// 		}
	// 	)
	// 		.then(function(response) {
	// 			if (!response.ok) {
	// 				throw Error(response.statusText);
	// 			}
	// 			return response.json();
	// 		})
	// 		.then(function(responseAsJson) {
	// 			console.log("responseAsJson", responseAsJson);
	// 			setTodos(responseAsJson);
	// 		})
	// 		.catch(function(error) {
	// 			console.log("Looks like there was a problem: \n", error);
	// 		});

	//filter cannot be a standalone function, it needs to be a variable example: var newTodos =
	//after filtering the function we needed to set the new todos to the updated (setTodos) so it can show the new
	//list of labels without the item we deleted
	// };

	//   export default class Demo extends React.PureComponent {
	//   constructor(props) {
	//     super(props);

	//     this.state = {
	//       data: appointments,
	//     };
	//   }

	//   render() {
	//     const { data } = this.state;
	//TURN THIS CLASS INTO A HOOK IN ORDER TO MAKE DATE NAVIGATION EASIER

	return (
		<>
			<Paper>
				<Scheduler data={events}>
					<ViewState currentDate={currentDate} />
					<MonthView startDayHour={7} endDayHour={20} />
					<Toolbar />
					<DateNavigator />
					<TodayButton />
					<Appointments />
				</Scheduler>
			</Paper>
		</>
	);
};

```