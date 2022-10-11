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


