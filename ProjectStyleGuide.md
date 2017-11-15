# Project Style Guide

## Table of Contents

- [Strings](#strings)
- [Variables](#variables)
- [Conditional Statements](#conditional-statements)
- [Properties](#properties)
- [Function Arguments](#function-arguments)
- [Destructuring](#destructuring)
- [Flow Types](#flow-types)
- [StyledComponents](#styled-components)
- [Miscellaneous](#miscellaneous)

### Strings

-   Use 'single quotes'.

-   Use string interpolation instead of appending the string.

-   Shouldn't use string refs -
    <https://reactjs.org/docs/refs-and-the-dom.html#legacy-api-string-refs>

-   Don’t use backticks (\` \`) if the length of the string is less..
    ```javascript
    // good
    const message='Hello User'
    
    // bad
    const message=`Hello User`
    ```
-   Check **undefined** for variables before accessing it.
    ```javascript
    // good
    const value = str.subStr()
    if(value){
        const newValue=value.subStr()
    }

    //bad
    const value = str.subStr()
    const newValue=value.subStr()
    ```
## Variables

-   Use proper variable names denoting what it actually does.

-   Use let and const as much as possible. If a variable value is never changed, use const. If it's an object whose keys or values for those keys are changed, it can still be declared as const.

## Conditional Statements

-   Use === and !== as much as possible.

-   Use curly braces for if statements. 
    ```    
    if(isAwesome){ return 1; }
    ```
-   Use logical OR, logical AND it will remove unnecessary if-else statement.

-   Inline If statements are not advised. Should be wrapped in {}
    ```javascript
    // good
    if (a!== b) { return }

    // bad
    if (a !=== b) return
    ```
## Properties

-   Use dot notation when accessing properties.

-   Use \[\] when accessing properties with a variable.

## Function Arguments

-   Don't reassign argument variables.
    ```javascript
    function fooBar(opt){ opt = 3; //wrong way of doing this. }
    ```
-   Functions should be arrow functions.

-   Avoid inline function.
    ```javascript
    // good
    handleClick =() =>{}
    <componentname onclick={this.handleClick}/>
     
    // bad
    <componentname onclick={()=>{}}/>
    ```
-   If a file has a single function/class, use default to export that function.

-   Use the same name for a function/class while doing both importing and exporting it to avoid confusion.
    ```js
       export default class componentname extends
        React.Component<> {render () {return()}} //correct
    ```
-   Don’t use an IIFE function
    ```javascript
    // good
     function () {this.someFunction()}
     someFunction= async()=> {}

     // bad
     (Async() => {} )() //inside a function
    ```
-   Use spread operator instead Object.assign
    ```js
    // good
    options=(...optionsDefault, ...options)

    // bad
    options =Object.assign({},optionsDefault, options)
    ```
-   Do not create side effect in the render function.

-   Keep standard name for the class and function, which represent their behaviour.
    ```
    // good
    handelClose, OverlayModal

    // bad
    closeClick, MainOverlayModal
    ```
## Destructuring

-   When using multiple variables from an Array or Object in many places, prefer destructuring.
    ```js
     const fullName = 'John Doe'; const [first, last] = fullName.split(''); //first = 'John' and last = 'Doe'
    ```
## Flow Types

-   Types should begin with a capital letter.

-   Do not use Any or Object as types. Always be more descriptive in such scenarios.

-   // @flow should be on top of the file.

-   Use shared flow type if it is required.

## StyledComponents: https://www.styled-components.com/

-   No hardcoded font-family and font-size, Should use a variable from a shared variables file.
    ```
    // good
    font-size: ${SC_REGULAR_SIZE_2}

    // bad
     font-size: 1.75em

    // good
    font-family: ${SC_LIGHT}

    // bad
    font-family: sc-sansLight
    ```
-   Color codes should not be hardcoded but should be configurable from a common file.
    ```
    // good
    color : ${RED_SCALE_COLOR_1}

    // bad
    color : red
    ```
-   Shouldn’t use any className attribute for the styled component.
    ```xml
    // good
    <Div>Hello</Div>
    
    // bad
    <Div className="abc">Hello</Div>
    ```
    Here Div is a styled component, so no need of use className prop to a styled component. Instead, same css properties of class “abc” can be placed as the css properties of the Style Component “Div” and no need of creating the class “abc”

-   Should not use Float css property because we are using Flex.
    ```
    // good
    Display:flex
    Justify-content:center
    //bad
    Float:left
    ```
-   Do not import external css, instead create a styled component with the styles. External css colours should be replaced with colours in colour.js file.

-   Remove IE8/9 related css from the external file

-   Remove webkit-box-sizing: border-box; -moz-box-sizing: border-box; browser related css. -webkit- not required ,styled component prefix automatically
    ```
    // good
    animation:

    // bad
    webkit-animation :
    ```
-   No inline styling
    ```js
    // good
    const TextArea = TextWrapper.extend`
                margin: 10px 30px 10px 20px;
                ${props => props.ReadonlyIcon && 'cursor: not-allowed'};`
    <TextArea ReadonlyIcon />
    
    // bad
    <TextArea style={ ReadonlyIcon}/>
    ```
-   When defining 0 as a value in css, you can omit the measurement metric.
    ```
    // good
    padding:0

    // bad
    Padding:0px
    ```
-   While creating the new colors or at the time of merging your code please check the existing color.js file, which helps to avoid duplicate color with different names.

## Miscellaneous

-   If you are using async and await, then Promise style ‘then’ and 'catch’ should be avoided.

-   In react, do not create new event handlers for render invocation. Instead, event handlers should be instance methods.

-   No comments or console.log statements should be present in the PR if it's not in a WIP state.

-   Routes should not have camelCase naming style. /core/LoginSuccess should be /core/login-success.

-   Use relative paths when importing other components or styles.

-   Add a line before and after every 'it' statement in a test case for better readability.

-   Use arrow functions instead of normal functions wherever you can.
    ```js
    // good
    const Myfunction=()=>{}

    // bad
    function Myfunction(){}
    ```
-   If some value has to be saved in a variable and the key for the variable is the same as the name of the variable, use ES6 like :
    ```
    const value = 1; const obj = { value }
    ```
-   If the contents of an arrow function has only a return statement,
    use it like this :
    ```js
    // good
    const bar = (x) => x\*2

    // bad
    const bar = (x) => { return x\*2 }
    ```
-   While using <src> tags, use the alt variable which describes what the image is for better a11y (accessibility requirements).
    ```
    // good
    alt="image not available"
    
    // bad
    alt=""
    ```
-   Use stateless component when not having states(function)

-   Use export when declaring the component than exporting component on next line.
    ```js
    // good
    export default class componentname extends React.Component<>
    {render () {return()}}
    
     // bad
    class componentname extends React.Component<> {render ()=>{return()}}
    export default componentname
    ```
-   No redundant code.

-   Filename and Export name must be the same.
    ```js
    // good
    export default RootHeader extends React 
    RootHeader.js//File name

    // bad
    export default RootHeader extends React
    CoreRootHeader.js//File name
    ```
-   Test case description should be proper. 
    ```
    it (“checks for component renders”)
    ```
-   Use ‘contains’ instead of ‘find’ in test cases.

-   Follow the same indentation rules throughout the code base.

-   There should be no warnings at the time of running test cases.

-   No warnings when displaying the output in browsers.

-   Even if the app is executing properly, test cases have to be completed.

-   The name of test file should the same as the file we are testing followed by .test. 
    ```
    test for page.js will be page.test.js
    ```
-   Package.lock.json should not have dependencies resolved from both artifactory & public npmjs registry. Recreate the file with artifactory as the source registry.
        Solution: The Package.lock.json have two different dependencies from which npm can refer to, to take any files or libraries registery which is public and artifactory which is internal.
    ```
    This dependency should be one, not two. Therefore deleted the Package.lock.json and did npm install 
    inside scb network to get the artifactory link only.
    ```
-   Use a TODO: marker with your bitbucket username whenever some code needs to be removed after another code is merged, so that we can track & revisit these: like I need a toaster to be displayed at the time of any service failure, so, for now, I have written alert which will be removed later by the toaster. In the stash will comment at that line number with TODO and my id and what is TODO.

-   Do not mutate the ‘event. Target’ values

-   Avoid importing unused files.

-   Empty props should be declared in all components for future use.
    ```ts
    // good
    type Props = {}
    ```
-   If any component has any activity on click of outside of the component container then there should be a test case related to document.addEventListener and document.removeEventListener

-   If the code is copied from somewhere then there should be comment link saying the code is referred from this link.

-   Initial state value should be set via a class property instead of the constructor as it is constantly initialized to the same value.
    ```js
    // good
    State = {
    visible: false
    }

    // bad
    constructor(props) {
    super(props);
    this.state.visible = false
    }
    ```
-   If the statement is long, then break it into smaller making it more readable.
    ```js
    // good
    const titleText = `Don't have a unique Email ID? Straight2Bank supports login via your registered email. If you do not have a registered email or if your email address is not unique, you may login
    with your Straight2Bank User ID.`  
           <Tooltip title={ titleText }></Tooltip>
    
     // bad
     <Tooltip title="Don't have a unique Email ID? Straight2Bank supports login via your registered email. If you do not have a registered email or if your email address is not unique, you may login with your Straight2Bank User ID."></Tooltip>
    ```
-   Write test cases for default Props also.

-   Make sure you have not left any preceding space.
    ```
    // good
    it(‘on click load component’)

    // bad
    it(‘ on click load component’)
    ```
-   You should have only one assertion per test. Make sure that the test describes accurately what you're testing. Also, make sure that you're providing least amount of information in the test.

-   Avoid Typo mistakes

-   Do not write any text “test” in description

-   Routing structure should match the folder structure.

-   Name should be accurate while using Link for routing(its match with the routing action)

-   Unit Test case for render is for particular HTML element not for styled component rendered.

-   Don’t use the on-click event un-necessary for react routing, Use react router Link.

-   Add a key attribute while iterating using “map” to avoid warning in the browser console.

-   If there is any duplicated code, refactor it by creating a new function.

-   In test Cases beforeEach, afterEach options are available. To initialize some values use beforeEach and to restore or delete some variables use afterEach.

-   Make sure that the test describes accurately what you're testing.
