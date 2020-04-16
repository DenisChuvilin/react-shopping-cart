At the end of this module, you should be able to:

    [::] describe what the Context API is and the problem is solves

        Context provides a way to share props without having to drill them through components

    [::] provide data to the component tree with a context provider and consume data from  a context object in nested components

        Step 1: Create - Create Context object in seperate file, dont forget to export

            import { createContext } from 'react';

            export const UserContext = createContext();

        Step 2: Provide - import createContext object and wrap the partent component with ContextObject.Provider, passing in as a prop the value you want the children of the parent component to share


            import {UserContext} from '../contexts/UserContext' - in file of interest

         return (
            <UserContext.Provider value={user}>
                <div className="container">
                    <User />
                </div>
            </UserContext.Provider>
            );

        Step 3: Consume - import your Context Object and consume the data you need from it

            import {UserContext} from "../../contexts/UserContext"

            function User() {

            const user = useContext(UserContext);

            return (
                <div className="profile">
                    <p>{user.lastName}, {user.firstName}</p>
                </div>
            );
            }

[::] Other notes:

        Redux uses context under the hood

        create context can be descructured 

            const { Provider, Consumer} = createContext();
        
        when you need to pass multiple state properties into the provider, you wrap your properties in an object and pass down 
            
            value = {{state, secondState }}

        when consuming from one of multiple states, you must first make reference to the state in an object

            <h1> {secondState.property.something} </>

                UserContext.Consumer wrap the data of choice when using the render method (ugly)
        
        We write capitalize our contexts because JSX assumes lowercase tags are html elements

            <userContext.Provider> will cause an error, must be <UserContext.Provider>
        
        When using the rendering method your callback inside your .Consumer will be set to your provider value