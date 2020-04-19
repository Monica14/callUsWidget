CallUsWidget 

To integrate this widget you will need to follow below steps : 

1.Add Below code in your HTML file

<div class="ads_callWidget" onclick="ads_callButton()">Call Us Now
    <span class="callWidgetContent" id="callWidgetBox"></span>
</div>

2. Import below css file
   Note :- file location can vary based on your folder structure for css 

<link rel="stylesheet" type="text/css" href="./callbutton.css" />

3. Add Below script to your file

    <script>
        // When the user clicks on widget button
        let ads_callButton = async () => {
            let buttonText = "No Text";
            let phone_number = "No Number";
            try {
                // Your link
                // const adrequest_url = new Request('https://codifyinditest.com/script_test/api-test'); // Able to access from browser but due to cors its not getting accessed  
                // Demo json link
                const adrequest_url = new Request('https://my-json-server.typicode.com/Monica14/callUsWidget/db'); // Demo link with same content of given api
                /**
                    Fetch Data from api to get details of call widget
                */
                const buttonData = await fetch(adrequest_url)
                    .then(response => {
                        return response.json();
                    })
                    .then(data => {
                        return data;
                    })
                    .catch(error => {
                        return error;
                    });

                buttonText = buttonData.script_test ? buttonData.script_test.labels : "No Text";
                phone_number = buttonData.script_test ? buttonData.script_test.phone_number : "No Number";

            }
            catch (e) {
                console.log("Error :", e);
            }
            var popup = document.getElementById("callWidgetBox");
            popup.classList.toggle("show");
            popup.innerHTML = `${buttonText} <br/> ${phone_number}`;
        }
    </script>

    4. Run the html file

