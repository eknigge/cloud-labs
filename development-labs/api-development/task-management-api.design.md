# Designing the REST API for a Task Management Application

> Hands-on Lab

|                   |                       |
| :---------------- | :-------------------- |
| Proficiency Level | **Cloud  Enthusiast** |
| Tags              | ![https://img.shields.io/badge/%20-API-blue](https://img.shields.io/badge/%20-API-blue) ![https://img.shields.io/badge/%20-Open%20API-blue](https://img.shields.io/badge/%20-Open%20API-blue) ![https://img.shields.io/badge/%20-Swagger-blue](https://img.shields.io/badge/%20-Swagger-blue)|

## Lab Scenario

In this lab, you will design the REST API for a Task Management application and describe it using an OpenAPI (aka Swagger) format.

[Swagger](https://swagger.io/) is a standard format to describe REST APIs that can be human-readble but also parsable by machine. Swagger can be used to automatically generate the subs for your API code.

## What will you learn in this lab?

After completion of this lab, you will be able to:

- Understand what is involved in the design of a REST API.
- Use Swagger to describe the API in a standard format.

## Prerequisites

To complete this lab, you will need the following:

- Reliable internet connection.
- Text editor of your choice.

## Lab Instructions

For the purpose of this lab, we will design a REST API that can manage tasks assigned to an user. Here are the requirements for the API.

### Requirements

- The API should be able to create, view, update, and delete *Users*.
- The API should be able to create, view, update, and delete *Tasks* assigned to users.
- A *Task* cannot be unassigned.

### Exercise #1: Design the Task Management API

In this exercise, you will design the Task Management API. The design can be written in a markdown document.

For the overall API, specify the following information:

- `Title` - this is the *Title* that should be used for the API Swagger document.
- `Contact Email` - this is the *Contact Email* that should be used in the Swagger document.
- `Host` - this should be the *Host* for the API endpoint in the Swagger document. Use `api.tasks.testsite01.com`
- `Schemes` - this is the *Scheme* that should be used in the Swagger document. Use `https`

For each resource and operation on a resource, specify the following information:

- `Path` - this is the path to the resource.
  - `Method` - the is the method used for the corresponding operation on the resource. For each method, list the following information:
    - `Summary` - this is a summary of the operation.
    - `OparationId` - this is an identifier of the operation.
    - `Parameters` - list all input parameters for the operation if any. For each parameter, list the following information:
      - `Location` - how the parameter is passed (`body`, `query`, `path`, etc.). This is the *in* in the Swagger document.
      - `Required` - whether the parameter is required or not (`true` or `false`).
      - `Type` - type of the parameter (`$ref`, `int`, `string`, etc).
    - `Responses` - list all possible responses from the operation. Each response should have:
      - `HTTP Response Code` - this is the HTTP response code.
      - `Description` - This is the optional message that will be send with the response code.
      - `Schema` - the *Schema* for the response. This will be the object that will be returned by the response.
- `Definitions` - the definition used by the operations. Each definition should have:
  - `Type` - the type of the definition
  - `Required Properties` - list of all the required properties.
  - `Properties` - the properties of the definition. Each property should have:
    - `Type` and `Format` for simple properties.
    - `$ref` for references to other definitions.
    - `items` for `array` properties.

Use the following table to aid your design:

| Path  | Create (`POST`)| Read (`GET`) | Update (`PUT`) | Update (`PATCH`) | Delete (`DELETE`) |
| ----- | ----- | ----- | ----- | ----- | ----- |
|  |  |  |  |  |  |

### Exercise #2: Create a Swagger Document for the Task Management API

In this exercise, you will use the information from the previous exercise to create a Swagger document for he Task Management API.

- Use the information from the previous exercise to describe the API in a standard Swagger format. You can use the [Swagger Editor](https://editor.swagger.io/) for that purpose.
- Save the resulting Swagger document in `YAML` format.

## Help improve this lab

[![Lab Issues](https://img.shields.io/github/issues/crimsonpinnacle/cloud-labs)](https://github.com/CrimsonPinnacle/cloud-labs/issues/new?assignees=toddysm&labels=new+lab&template=bug_template.md&title=) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/CrimsonPinnacle/cloud-labs/pulls)