function checkCashRegister(price, cash, cid) {
  let change = cash - price;
  let outArr = [];
  let result = {
    status: "OPEN",
    change: outArr,
  };
  let cidObj = {};

  for (var i = 0; i < cid.length; i++) {
    for (var j = 0; j < cid[i].length; j++) {
      cidObj[cid[i][0]] = cid[i][1];
    }
  }
  let tillAmount = cid.flat().filter(function (val) {
    if (typeof val === "number") {
      return val;
    }
  });

  let totalInTill = round(tillAmount.reduce((a, b) => a + b));
  if (change > totalInTill) {
    result.status = "INSUFFICIENT_FUNDS";
    result.change = [];
    return result;
  }
  if (change === totalInTill) {
    result.status = "CLOSED";
    result.change = cid;
    return result;
  }
  //add result status and array at the end, but save the data in var.
  if (change <= totalInTill) {
    if (change / 100 > 0 && cidObj["ONE HUNDRED"]) {
      let hundred = cidObj["ONE HUNDRED"] / 100;
      let changeHundred = Math.floor(change / 100);

      if (hundred <= changeHundred) {
        outArr.push(["ONE HUNDRED", cidObj["ONE HUNDRED"]]);
        change = round(change - cidObj["ONE HUNDRED"]);
        
      }
      if (hundred > changeHundred) {
        let diff = hundred * 100 - (hundred * 100 - changeHundred * 100);
        if (diff > 0) {
          outArr.push(["ONE HUNDRED", diff]);
        }
        change = round(change - diff);
      }
    }
    if (change / 20 > 0 && cidObj["TWENTY"]) {
      //divide cidObj twenty by 20 to find out how many 20s.
      let twenties = cidObj["TWENTY"] / 20;
      let changeTwenty = Math.floor(change / 20);

      if (twenties <= changeTwenty) {
        outArr.push(["TWENTY", cidObj["TWENTY"]]);
        change = round(change - cidObj["TWENTY"]);
  
      }
      if (twenties > changeTwenty) {
        let diff = twenties * 20 - (twenties * 20 - changeTwenty * 20);
        if (diff > 0) {
          outArr.push(["TWENTY", diff]);
        }
        change = round(change - diff);
      }
    }
    if (change / 10 > 0 && cidObj["TEN"]) {
      let ten = cidObj["TEN"] / 10;
      let changeTen = Math.floor(change / 10);

      if (ten <= changeTen) {
        outArr.push(["TEN", cidObj["TEN"]]);
        change = round(change - cidObj["TEN"]);
      }
      if (ten > changeTen) {
        let diff = ten * 10 - (ten * 10 - changeTen * 10);
        if (diff > 0) {
          outArr.push(["TEN", diff]);
        }
        change = round(change - diff);
      }
    }
    if (change / 5 > 0 && cidObj["FIVE"]) {
      let five = cidObj["FIVE"] / 5;
      let changeFive = Math.floor(change / 5);

      if (five <= changeFive) {
        outArr.push(["FIVE", cidObj["FIVE"]]);
        change = round(change - cidObj["FIVE"]);
      }
      if (five > changeFive) {
        let diff = five * 5 - (five * 5 - changeFive * 5);
        if (diff > 0) {
          outArr.push(["FIVE", diff]);
        }
        change = round(change - diff);
      }
    }
    if (change / 1 > 0 && cidObj["ONE"]) {
      let one = cidObj["ONE"] / 1;
      let changeOne = Math.floor(change / 1);

      if (one <= changeOne) {
        outArr.push(["ONE", cidObj["ONE"]]);
        change = round(change - cidObj["ONE"]);
      }
      if (one > changeOne) {
        let diff = one * 1 - (one * 1 - changeOne * 1);
        if (diff > 0) {
          outArr.push(["ONE", diff]);
        }
        change = round(change - diff);
      }
    }
    if (change / 0.25 > 0 && cidObj["QUARTER"]) {
      let quart = cidObj["QUARTER"] / 0.25;
      let changeQuart = Math.floor(change / 0.25);

      if (quart <= changeQuart) {
        outArr.push(["QUARTER", cidObj["QUARTER"]]);
        change = round(change - cidObj["QUARTER"]);   
      }
      if (quart > changeQuart) {
        let diff = quart * 0.25 - (quart * 0.25 - changeQuart * 0.25);
        if (diff > 0) {
          outArr.push(["QUARTER", round(diff)]);
        }
        change = round(change - diff);
      }
    }
    if (change / 0.1 > 0 && cidObj["DIME"]) {
      let dime = cidObj["DIME"] / 0.1;
      let changeDime = Math.floor(change / 0.1);

      if (dime <= changeDime) {
        outArr.push(["DIME", cidObj["DIME"]]);
        change = round(change - cidObj["DIME"]);
      }
      if (dime > changeDime) {
        let diff = dime * 0.1 - (dime * 0.1 - changeDime * 0.1);
        if (diff > 0) {
          outArr.push(["DIME", round(diff)]);
        }
        change = round(change - diff);
      }
    }
    if (change / 0.01 > 0 && cidObj["PENNY"]) {
      let penny = cidObj["PENNY"] / 0.01;
      let changePenny = Math.floor(change / 0.01);

      if (penny <= changePenny) {
        outArr.push(["PENNY", cidObj["PENNY"]]);
        change = round(change - cidObj["PENNY"]);
      }
      if (penny > changePenny) {
        let diff = penny * 0.01 - (penny * 0.01 - changePenny * 0.01);
        if (diff > 0) {
          outArr.push(["PENNY", round(diff)]);
        }
        change = round(change - diff);
      }
    }
    if (change) {
      result.status = "INSUFFICIENT_FUNDS";
      result.change = [];
      return result;
    }
  }
  return result;
}
function round(value, decimals = 2) {
  return Number(Math.round(value + "e" + decimals) + "e-" + decimals);
}
