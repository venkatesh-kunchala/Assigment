# Assigment
const COMMA_ENTRIES = [ // First name, City, Birth date
  'Mckayla, Atlanta, 5/29/1986',
  'Elliot, New York City, 4/3/1947',
]
const DOLLAR_ENTRIES = [ // City, Birth date, Last name, First name
  'LA $ 10-4-1974 $ Nolan $ Rhiannon',
  'NYC $ 12-1-1962 $ Bruen $ Rigoberto',
]

class App {
  static run({ comma = [], dollar = [] }) {
    // INVOKE YOUR MAGICAL CODE HERE
    
    //Remove comma symbol
    
    let commaEntries = comma.map((item) => item.split(","));
		
    //Updating the final output as we require
    
		let updatedCommaEntries = commaEntries.map((item) => {
  		let val = "";
  		return item.reduce((val, innerItem) => val + innerItem);
		});
		

		//Remove dollar symbol
    
    let dollarEntries = dollar.map((item) => item.split("$"));

		//Removing last name and updating as we require in the output
    
		let updatedDollarEntries = dollarEntries.map((item) => {
  		return item[3].trim() + " " + item[0].trim() + " " + item[1].trim().replace(/-/g,"/");
		});
    
    //Printing as per excepted standard output
    
    for(let i=0,j=0;i<updatedCommaEntries.length,j<updatedDollarEntries.length;i++,j++){
    	console.log(updatedCommaEntries[i]);
      console.log(updatedDollarEntries[j]);
    }
    
  }
}

App.run({ comma: COMMA_ENTRIES, dollar: DOLLAR_ENTRIES })
// Expected standard output:
//   Mckayla Atlanta 5/29/1986
//   Rhiannon Los Angeles 10/4/1974
//   Elliot New York City 4/3/1947
//   Rigoberto New York City 12/1/1962

// WRITE YOUR SPECS HERE
