- Will be using aNewSpring.
- Sage Integrations - currently on hold.
- Auth systems - SAML SSO.
- TIS.
- No touch points as of yet.
- Plugin - Classroom + Historical data and some other things, will chat to Trin around this tomorrow.
# Classroom Plugin 
- Implemented by using Javascript in a course's content to manipulate aNewSpring UI. 
- The j.s executed in an html content type.
	- It selects elements on the DOM and removes them completely, and then replaces content on the page with our project content
	  which is also programmed using html, css, js etc. 
- To do this we can follow these steps:
	1. Navigate to the Ampath Template:
	![[Pasted image 20240313092811.png]]
	2. Click on 'Edit' and then go to the block's settings tab:
	![[Pasted image 20240313092919.png]]
	3. In the above, we will be using the Block explanation header to target and replace with our code. 
	4. Once in the block settings we will go to the explaination of block section and add the content part that will house our js code. 
	![[Pasted image 20240313093227.png]]
	5. Click on change and it'll take you to the below page where we can then edit the script, we can +content part and then click update:
	![[Pasted image 20240313093548.png]]
	6. This gives us the place where we write the script: 
	![[Pasted image 20240313093651.png]]
	Essentially what we are doing here is creating a Template, adding a block and then using the blocks explanation section as a target, we then add a content part to this section. 
	In the content part we use a script that selects the heading section by it's html/css tags and classes and use javascript to replace the content with what we want to see. 
	
	There are some nuances to how this works, for example you will need to look up the shadowroot and how that works so that things like bootstrap versions etc do not clash with what the aNS system is using internally when rendering their usual content on aNS 

# Notes summary 
- 3 Programs
	1. Billing accounts receivable 
	2. Point of Care 
	3. Cashiering
	All resources for these programs are stored on google and are accessible to learners of the program.
- 2 e-forms
	- Attendance form
	- Observation form(filled out at the end)
	These are condensed into one final form for all 3 programs
- Grade response sheet. 
	- Each program is linked to its own response sheet. 
- Workday: 
	- The following is updated: 
		Program scheduling, 
		Enrolment,
		Attendance and grading

- One platform for all our training needs and not Workday and *Our Portfolio can be up to 150 pages thus it is a huge size which Workday can currently not accommodate therefor we use the google drive - we would like to link each one of these portfolios to the relevant users worker documents. 
- Managers should have access to all training certificates and worker documents. 
- Outcomes should be listed as Competent or not yet competent. Please not pass or failed! 
- Should be able to get a report per month for statistical purposes - currently we update it manually. Example the nr of employees who attended the courses per month - sent automatically via email. 
	- Be able to draw an annual report with all the statistics. 
- Be able to draw an attendance register for a specific period of time if needed
# Requirements of custom Classroom plugin

Meeting Notes: https://app.diagrams.net/#G19EieO0XWacRUxzykKl6We_W-z0jjctd2#%7B%22pageId%22%3A%226yLlTRfnzJYRCMVadLyJ%22%7D
```
1. Training Vs Training Categories :  
- Billing Account Receivable  
- Point Of Care  
- Cashiering  
2. Training has Training Materials  
3. Learners have access to training materials (but when??)  
4. Learners Complete Feedback and attendance  
5. Handouts:  
- Documents that will be distributed during class (i.e activities)  
- Technical Classroom activities  
- Result documents  
- Certificate of attendance  
- Signed Competency document  
  
6. Only one platform can be used  
7. Managers will have access to all training certificates and workers documents*  
8. Outcome type should be : competent or Not yet Competent  
9. Monthly and annual reports  
10. Attendance Register
```


# Current script

```js
<script>
// Get the div element by its class name
var div = document.querySelector('.ans-structure-big');

// Remove all child elements of the div
while (div.firstChild) {
  div.removeChild(div.firstChild);
}
var contentContainer = div;
const shadowRoot = contentContainer.attachShadow({ mode: 'open' });
 var  pageContent ="";
// Use the fetch API to load the external HTML content
fetch('https://nlt-classroom.azurewebsites.net/')
  .then(response => response.text())
  .then(htmlContent => {
    // Insert the loaded content into the shadow DOM
    const contentWrapper = document.createElement('div');

    var content = `
      <style>
        <link href="https://nlt-classroom.azurewebsites.net/Content/css?v=-ajo3J6QtgGZONnv3AZei244jm7A7pCtHShB7DstoFM1"/>
      </style>
    `;
    content = content + htmlContent;

    contentWrapper.innerHTML = content;
    shadowRoot.appendChild(contentWrapper);

    // Find elements inside the shadow DOM
      pageContent = shadowRoot.getElementById('PageContectSection');
    loadSchedules()
})
  .catch(error => {
    console.error('Error loading external content: ', error);
  });
     //---------------------------------------------------------------------
    function ClearPageContent() {
        while (pageContent.firstChild) {
            pageContent.removeChild(pageContent.firstChild);
        }
    }
    //---------------------------------------------------------------------
    function BuildMainHeader(titleText)
    {
        //------------ Create Main Row
        const row = document.createElement('div');
        const headerColDiv = document.createElement('div');
        const buttonColDiv = document.createElement('div');
        const header = document.createElement('h5');
        const addButton = document.createElement('button');
        const hr = document.createElement('hr');
        //-------------------------------------------------
        row.className = 'row';
        headerColDiv.className = 'col';
        buttonColDiv.className = 'col-1';
        addButton.className = 'btn btn-secondary';
        header.textContent = titleText
        //-------------------------------------------------
        header.style.cssText = 'margin-top: 15px;';
        addButton.style.cssText = '--bs-btn-font-size: .75rem;';
        addButton.textContent = 'Add';
        //-------------------------------------------------
        buttonColDiv.appendChild(addButton);
        headerColDiv.appendChild(header);
        row.appendChild(headerColDiv);
        row.appendChild(buttonColDiv);
        pageContent.appendChild(row);
        pageContent.appendChild(hr);
    }
    function BuildTable(headers,data) {
        //------------ Create Main Row
        const table = document.createElement('table');
        const thead = document.createElement('thead');
        const headerRow = document.createElement('tr');
        const tbody = document.createElement('tbody');
        //-------------------------------------------------
        table.id = '';
        table.className = 'table';
        table.style.width = '100%';
        //-------------------------------------------------
        headers.forEach(headerText => {
            const header = document.createElement('th');
            header.textContent = headerText;
            headerRow.appendChild(header);
        });
        //-------------------------------------------------
        data.forEach(data => {
            //---------------------------------------------
            const row = document.createElement('tr');
            //---------------------------------------------
            data.forEach(value => {
                const cell = document.createElement('td');
                cell.width = '20%';
                cell.textContent = value;
                row.appendChild(cell);
            });
            //--------------------------------------------
            const actionsCell = document.createElement('td');
            const viewButton = document.createElement('button');
            //--------------------------------------------
            viewButton.type = 'button';
            viewButton.className = 'btn btn-secondary';
            viewButton.style.cssText = '--bs-btn-padding-y: .25rem; --bs-btn-padding-x: .5rem; --bs-btn-font-size: .75rem;';
            viewButton.textContent = 'View';
            actionsCell.appendChild(viewButton);
            row.appendChild(actionsCell);
            //--------------------------------------------
            tbody.appendChild(row);
        });
        //------------------------------------------------
        thead.appendChild(headerRow);
        table.appendChild(thead);
        table.appendChild(tbody);
        pageContent.appendChild(table);
        //------------------------------------------------
    }
    //---------------------------------------------------------------------

    //---------------------------------------------------------------------
    function loadHome()
    {
        ClearPageContent();
    }
    //---------------------------------------------------------------------
    function loadSchedules()
    {
        ClearPageContent();
        const trainingHeaders = ['Training Code', 'Training Name', 'Start Date', 'End Date', 'Action'];
        const trainingData = [
            ['001', 'Training 1', '11/02/2023', '15/02/2023'],
            ['002', 'Training 2', '11/02/2023', '15/02/2023'],
            ['003', 'Training 3', '11/02/2023', '15/02/2023'],
        ];
        BuildMainHeader("Schedule List")
        BuildTable(trainingHeaders, trainingData)
    }
    //---------------------------------------------------------------------
    function loadTrainings()
    {
        ClearPageContent();
        const trainingHeaders = ['Training Code', 'Training Title', 'Category', 'Action'];
        const trainingData = [
            ['001', 'Training 1', 'Billing Account Receivable'],
            ['002', 'Training 2', 'Point Of Care'],
            ['003', 'Training 3', 'Cashiering'],
        ];
        BuildMainHeader("Training List")
        BuildTable(trainingHeaders, trainingData)
    }
    //---------------------------------------------------------------------
    function loadLearners()
    {
        ClearPageContent();
        const trainingHeaders = ['First Name', 'Last Name', 'Email', 'Action'];
        const trainingData = [
            ['Kyle', 'Routledge', 'Kyle@newleaftech.co.za'],
            ['Collen', 'Mashamba', 'Collen@newleaftech.co.za'],
            ['Matt', 'Hanly', 'Matt@newleaftech.co.za'],
        ];
        BuildMainHeader("Learner List")
        BuildTable(trainingHeaders, trainingData)
    }
    //---------------------------------------------------------------------
    
    //---------------------------------------------------------------------
</script>
```