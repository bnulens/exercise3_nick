## We added comments to the JS of Nick
___
// Constructor for Person
function Person(image,first,last,age,food){
    this.image = image;
    this.firstName = first;
    this.lastName = last;
    this.age = age;
    this.food = food;
    
// first mention of addInfo referring to the function 
    addInfo(first,this)

    document.getElementById(first+"Button").addEventListener('click',toggle);

// function to activate toggle for Images inside the family card 
    function toggle(){
        console.log('works!')
        let image = document.getElementById(first+'Img');
        if(image.style.display == "block"){
            image.style.display = "none";
        }else{
            image.style.display = "block";
        }
    }
}

// create people based on Person constructor
let father = new Person("images/father.jpg","Rudi","Banken","53","Fries");
let mother = new Person("images/mother.jpg","Heidi","Vissers","49","Fishsteak");
let sister = new Person('images/sister.jpg','Katja','Banken','29','Chinese');
let brother = new Person("images/father.jpg","Ben","Banken","23","Fries");
let stepMom = new Person("images/mother.jpg","Fabienne","Motmans","52","Veggies");
let stepSister = new Person('images/sister.jpg','Jessy','Raemakers','36','Shushi');

//  addinfo function invokes the firstName from the Person constructor
function addInfo(member,object){

    // creating an element "div" dynamically with class "card"
    let div = document.createElement('div'); 
    div.setAttribute('class','card');
    div.setAttribute('id',member)
    // creating an unordered list dynamically with a loop for adding people 
    // based on the constructor (index).
    let ul = document.createElement('ul');
   
    // start of loop with index being Person 
    for(var i in object){

        let li = document.createElement('li')

        // looking at the first 6 characters to specify an image 
        if(typeof object[i] == 'string'){
            var firstChars = object[i].substring(0,6);
        }
        ;
        
        // condition if the first characters are -i,m,a,g,e,s- 
        if (firstChars == 'images'){
            
            // if statement is TRUE we create an "img" element 
            let image = document.createElement("img")
            // adding the source to the image based on the index of Person
            image.setAttribute('src', object[i]);
            // adding alt text
            image.setAttribute('alt', member);
            // escribing ID to set Person with set "img" 
            image.setAttribute('id',member+'Img');
            // by default the image will be displayed 
            image.setAttribute('style','display:block')
            // put the "image" inside the "li"
            li.append(image);
            // put the "li" inside the "ul"
            ul.append(li);
        
        // if the condition is False the "li" will still be created without the "img"
        }else{
            
            li.innerHTML = `${i}: ${object[i]}`;
            
            ul.append(li);
        }
      
    }
    
    // we select the element "id" with name "row" and immediately put the "div" we made earlier
    // and put it inside the "row".
    document.getElementById('row').appendChild(div);
    // the created "ul" will be put inside the "div"
    div.append(ul);

    // a button will be made 
    let button = document.createElement('button')
    // the button will have the "id" with name of the familymember 
    button.setAttribute('id',member+'Button');
    // the text of set button will be "Click me"
    button.innerHTML = 'Click me';
    // lastly the toggle button will be added inside the dynamically created div
    div.append(button);
}
