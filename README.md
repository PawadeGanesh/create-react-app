# create-react-app
setting up the react-app


#array filtering and map dynamically in js:
const data = [
    {
      part: 'LM',
      section: '021',
      column: '001',
      description: 'Descrizione attività/passività',
      type: 'NUM'
    },
    {
      part: 'LM',
      section: '021',
      column: '002',
      description: 'Assenza cause Ostative Applicazione Regime',
      type: 'CB'
    },
    {
      part: 'LM',
      section: '042',
      column: '001',
      description: 'Differenza su reddito',
      type: 'NUM'
    },
    {
      part: 'LM',
      section: '050',
      column: '006',
      description: 'Perdite non compensate - Eccedenza 2018',
      type: 'NUM'
    }
  ];

  const output = Object.values(
    data.reduce((b, a) => {
      if (b.hasOwnProperty(a.section)) b[a.section].columns.push(a.column);
      else {
        a.columns = [a.column];
        b[a.section] = a;
      }
      return b;
    }, {})
  );
  // console.log(output);
  
  
  
  
  
  #creating dynamic text field in array on click of button:
  import React, { useState } from 'react';

function App() {
  const [inputList, setInputList] = useState([{ firstName: '', lastName: '' }]);

  // handle input change
  const handleInputChange = (e, index) => {
    const { name, value } = e.target;
    const list = [...inputList];
    list[index][name] = value;
    setInputList(list);
  };

  // handle click event of the Remove button
  const handleRemoveClick = (index) => {
    const list = [...inputList];
    list.splice(index, 1);
    setInputList(list);
  };

  // handle click event of the Add button
  const handleAddClick = () => {
    setInputList([...inputList, { firstName: '', lastName: '' }]);
  };

  return (
    <div className="App">
      <h3>
        <a href="https://cluemediator.com">Clue Mediator</a>
      </h3>
      {inputList.map((x, i) => {
        return (
          <div className="box">
            <input
              name="firstName"
              placeholder="Enter First Name"
              value={x.firstName}
              onChange={(e) => handleInputChange(e, i)}
            />
            <input
              className="ml10"
              name="lastName"
              placeholder="Enter Last Name"
              value={x.lastName}
              onChange={(e) => handleInputChange(e, i)}
            />
            <div className="btn-box">
              {inputList.length !== 1 && (
                <button className="mr10" onClick={() => handleRemoveClick(i)}>
                  Remove
                </button>
              )}
              {inputList.length - 1 === i && (
                <button onClick={handleAddClick}>Add</button>
              )}
            </div>
          </div>
        );
      })}
      <div style={{ marginTop: 20 }}>{JSON.stringify(inputList)}</div>
    </div>
  );
}

export default App;



