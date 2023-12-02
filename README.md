function BankAccount(accountNumber, name, type, balance) {
  this.accountNumber = accountNumber;
  this.name = name;
  this.type = type;
  this.balance = balance;
}

BankAccount.prototype.deposit = function(amount) {
  this.balance += amount;
};

BankAccount.prototype.withdraw = function(amount) {
  if (this.balance >= amount) {
    this.balance -= amount;
  }
};

BankAccount.prototype.checkBalance = function() {
  console.log(this.balance);
};

BankAccount.prototype.isActive = function() {
  return this.balance > 0;
};

function getTotalBalance(accounts) {
  let totalBalance = 0;
  for (let account of accounts) {
    if (account.isActive()) {
      totalBalance += account.balance;
    }
  }
  return totalBalance;
}

// Create multiple BankAccount objects representing different accounts
let acc1 = new BankAccount(1, "John Doe", "Saving", 1000);
let acc2 = new BankAccount(2, "Jane Smith", "Checking", 500);
let acc3 = new BankAccount(3, "Bob Johnson", "Saving", 1500);

// Perform a series of deposit, withdrawal, and balance check operations on these accounts
acc1.deposit(500);
acc2.withdraw(200);
acc3.checkBalance();

// Test the isActive method to check if the accounts are active
console.log(acc1.isActive());
console.log(acc2.isActive());
console.log(acc3.isActive());

// Test the getTotalBalance function to display the total balance of all active accounts
let allAccounts = [acc1, acc2, acc3];
console.log(getTotalBalance(allAccounts));
