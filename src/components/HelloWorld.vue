<template>
  <div class="Hello World">
    <h1>{{ msg }}</h1>
  </div>
  <div class="card">
    <h2>New York Rangers</h2>
    <img alt="real estate logo" src="https://elitesportsny.com/wp-content/uploads/2019/02/gettyimages-56613588-2-1362x766.jpg">
    <div class="card-content">  
      <p id="description">On this card, there is an iconic picture of the New York Rangers Stanley Cup win in 1994. This was the last time they won the Stanley Cup, where they bested the Vancouver Canucks in a seven-game series. They won with an electric goal in overtime of game 7, which resulted in a final score of 2-1 Rangers.</p> 
      <button class="details-button" id="detailsBtn">Details</button>
    </div> 
  </div> 
  
  <button id="btn">Duplicator</button>
  <button id="colorBtn">BGColorChanger</button>
  <button id="Headingbtn">HeadingChanger</button>
  <button id="dltbtn">DeleteCard</button>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  mounted() {
    document.querySelector('#btn').addEventListener('click', () => {
      const clone = document.querySelector('.card').cloneNode(true); // Clone the whole card
      document.body.appendChild(clone);
    });
    
    var numbers = ["1", "2", "3", "4", "5", "6", "7", "8", "9"];
    var letters = ["A", "B", "C", "D", "E", "F"];
    
    function randomColor() {
      var color = "";
      for (var i = 0; i < 3; i++) {
        var index = Math.floor(Math.random() * (numbers.length + letters.length));
        color += (index < numbers.length) ? numbers[index] : letters[index - numbers.length];
      }
      return color;
    }
    
    document.querySelector('#colorBtn').addEventListener('click', () => {
      const card = document.querySelector('.card');
      // Change background color
      card.style.backgroundColor = '#' + randomColor();
    });
    
    // HEADING CHANGER
    document.querySelector('#Headingbtn').addEventListener('click', () => {
      const title = document.querySelector('h2');
      title.innerText = "New York Rangers Win!";
    });
    
    // Card delete
    document.querySelector('#dltbtn').addEventListener('click', () => {
      const cards = document.querySelectorAll('.card');
      // Check if there are cards to delete
      if (cards.length > 1) {
        const lastCard = cards[cards.length - 1];
        lastCard.parentNode.removeChild(lastCard);
      }
    });
    
    var original = document.querySelector('#description').innerText;
    
    document.querySelector('#detailsBtn').addEventListener('click', () => {
      const description = document.querySelector('#description');
      // Toggle the visibility of the description
      if (description.innerText === 'none' || description.innerText === '') {
        description.innerText = original; // Show the description
      } else {
        description.innerText = ''; // Hide the description
      }
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card {
  max-width: 400px;
  margin: 0 auto;
  border: 3px solid #000000;
  background-color: #848484;
  padding: 16px;
  display: flex;
  flex-direction: column;
  text-align: center;
}

.card img {
  max-width: 100%;
  height: auto;
}

.card-content {
  flex: 1;
}

/* Style for the Title label */
h2 {
  font-size: 24px;
  margin: -10px 0;
  /* Background color and border */
  color: #fff;
  /* Text color on the background */
  padding: 8px 16px;
  border-radius: 4px;
}

p {
  font-size: 16px;
  margin: 8px 0;
  color: #fff;
}

a.details-button {
  color: #fff;
  padding: 8px 16px;
  text-decoration: none;
  border-radius: 4px;
}
</style>
