## EmployeeDetailsStorage-Using-Blockchain
To store employee details in a blockchain using solidity, truffle, ganache and metamask.

# Set of Commands:
  const { Details } = require("@mui/icons-material")

  truffle compile
  truffle migrate --reset --network development
  truffle console --network development

# Get a deployed instance:
  const employeeDetails = await EmployeeDetails.deployed();

# Set an employee Details:
  await employeeDetails.setEmployee(1, "John Doe", 30, "Engineer");

#  Get the Details:
  const employee = await employeeDetails.getEmployee(1);
  console.log(employee);

#  Update the details:
  await employeeDetails.updateEmployee(1, "John Doe", 31, "Senior Engineer");

#  Verifying the update:
  const updatedEmployee = await employeeDetails.getEmployee(1);
  console.log(updatedEmployee);


# Testing the contract:
  const EmployeeDetails = artifacts.require("EmployeeDetails");
  
  contract("EmployeeDetails", (accounts) => {
    it("should set and get employee details", async () => {
      const employeeDetails = await EmployeeDetails.deployed();
      
      await employeeDetails.setEmployee(1, "Alice", 28, "Developer");
      const employee = await employeeDetails.getEmployee(1);
      
      assert.equal(employee[0], "Alice", "Name should be Alice");
      assert.equal(employee[1].toNumber(), 28, "Age should be 28");
      assert.equal(employee[2], "Developer", "Position should be Developer");
    });
  });
