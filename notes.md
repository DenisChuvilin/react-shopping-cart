At the end of this module, you should be able to:

    [::] describe what the Context API is and the problem is solves

        Context provides a way to share props without having to drill them through components

    [::] provide data to the component tree with a context provider and consume data from  a context object in nested components

        Step 1: Create - Create Context object

            import { createContext } from 'react';

            const UserContext = createContext();

        Step 2: Provide - import createContext object and wrap the partent component with ContextObject.Provider, passing in as a prop the value you want the children of the parent component to share

            export const UserContext = createContext(); - in seperate file

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
