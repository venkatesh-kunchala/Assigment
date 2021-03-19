# Assigment

const COMMA_ENTRIES = [ // First name, City, Birth date
  'Mckayla, Atlanta, 5/29/1986',
  'Elliot, New York City, 4/3/1947',
]
const DOLLAR_ENTRIES = [ // City, Birth date, Last name, First name
  'LA $ 10-4-1974 $ Nolan $ Rhiannon',
  'NYC $ 12-1-1962 $ Bruen $ Rigoberto',
]

class Formator {
        //constructor

  constructor (stringList)
  {
    this.format_stringList = stringList;
    this.formator = [];
  }

       //format Function of deleting symbols like , and $ of original array to an array of words

	format(element)
  {
    this.format_stringList.forEach((str, index) => {
      this.formator[index] = str.split(element)
    })
  }

        //getting data from App class as storing an array of having firstname,city and date

  customizeFormat (c_fun) 
  {
    this.formator = c_fun(this.formator);
  } 
  
        //Printing function of modified data as output

  log() {
    console.log(this.formator);
  } 
}

class App {
  static run({ comma = [], dollar = [] }) {
    // INVOKE YOUR MAGICAL CODE HERE
    const commaObj = new Formator(comma);
    const dollarObj = new Formator(dollar);

    commaObj.format(",");
    dollarObj.format("$");

    //Pass your custom arrray of words as callback to customize_Format 
     dollarObj.customizeFormat(list_strs => {
      let outputstring = [];
      for(const [index, wordList] of list_strs.entries()){
        outputstring[index] = [wordList[3], wordList[0], wordList[1].replace(/-/g, "/")]
      }
      return outputstring;
    });
   
    commaObj.log();
    dollarObj.log(); 
  }
}

App.run({ comma: COMMA_ENTRIES, dollar: DOLLAR_ENTRIES })
// Expected standard output:
//   Mckayla Atlanta 5/29/1986
//   Rhiannon Los Angeles 10/4/1974
//   Elliot New York City 4/3/1947
//   Rigoberto New York City 12/1/1962

// WRITE YOUR SPECS HERE
