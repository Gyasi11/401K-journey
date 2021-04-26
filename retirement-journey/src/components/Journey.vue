<template>
<div>
    <h2>Your Financial Journey</h2>
    <div class="form-container">
        <form action="">
            <h3>Deposited Dollars</h3>
            <input v-model="depositedDollars" type="text">
            <h3>Amount of years vested</h3>
            <input v-model="nper" type="text">
            <button v-on:click="retirementResult()" id="submit-button" type="button">Take Action</button>
        </form>

        <h4> {{ futureValue }} </h4>
    </div>

    <div class="iconContainer">
        <img v-bind:style="styleObject" class="vehicleIcon" src="../assets/vehicle.png" alt="">
    </div>

    <div class="iconPathContainer">
        <div class="lineOne"></div>
        <div class="lineTwo"></div>
        <div class="lineThree"></div>
    </div>

</div>
</template>

<script>
export default {
    name: 'Journey',
    data: function () {
        return {
            futureValue: 0,
            depositedDollars: 0,
            interestRate: .05,
            nper: 0,
            styleObject: {
                left: '0px',
                position: 'relative'
            }
        }
    },
    methods: {
        retirementResult() {
            this.futureValue = this.depositedDollars * (Math.pow(1 + this.interestRate, this.nper) - 1) / this.interestRate
            this.futureValue = Math.round(this.futureValue)
            if (this.futureValue >= 1000) {
                this.futureValue = (this.futureValue / 100000) * 100;
                this.futureValue = Math.floor(this.futureValue)
                console.log(this.futureValue)
                this.styleObject.left = this.futureValue.toString() + "px"
            } else  if (this.futureValue == 0) {
                this.styleObject.left == '0px'
            }
            return this.futureValue
        }
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.form-container {
    height: 500px;
    width: 500px;
    min-width: 350px;
}

form {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

h3 {
    font-size: 24px;
}

h4 {
    margin-top: 48px;
}

input {
    display: block;
    width: 100px;
    border: none;
    border-bottom: 1px solid #bfbfbf;
    background: 0;
    font-size: 24px;
    padding-top: 24px;
}

#submit-button {
    padding: 20px;
    width: 200px;
    border-radius: 10px;
    border: none;
    margin-top: 48px;
    font-size: 14px;
    background-color: #3C66F9;
    color: #fafafa;
}

#submit-button:hover {
    cursor: pointer;
}

.vehicleIcon {
    width: 15%;
    transition: all 0.5s ease;
}

.iconContainer {
    display: flex;
}

.iconPathContainer {
    display: flex;
    flex-direction: row;
}

.lineOne {
    width: 25%;
    border-top: 4px yellow solid;
}

.lineTwo {
    width: 50%;
    border-top: 4px blue solid;
}

.lineThree {
    width: 25%;
    border-top: 4px green solid;
}
</style>
