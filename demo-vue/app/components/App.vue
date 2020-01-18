<template>
  <Page>
    <ActionBar title="Local Notifications demo"></ActionBar>

    <StackLayout>
      <Button @tap="onTapHasPermission" class="btn" text="Has Permission?"></Button>
      <Button @tap="onTapScheduleNotification" class="btn" text="Schedule Notification1"></Button>
      <Button @tap="onTapCancelAll" class="btn" text="Cancel notifications"></Button>
      <Label class="message" :text="message" textWrap="true"></Label>
    </StackLayout>
  </Page>
</template>

<script>
  import { alert } from "tns-core-modules/ui/dialogs";
  import { Color } from "tns-core-modules/color";
  import { LocalNotifications } from "nativescript-local-notifications";
  

  export default {


    created() {
      LocalNotifications.addOnMessageReceivedCallback(notificationData => {
        this.message = "Notification received: " + JSON.stringify(notificationData);
      });
    },

    data() {
      return {
        message: "Tap a button above..",
        alertNumber: 2,
        localPrayers: [],
        prayers: 

        [
          {
              id: 1,
              title: 'X1?',
              subtitle: 'This poster is awesome!',
              body: 'The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app.',
              bigTextStyle: false, // Allow more than 1 row of the 'body' text on Android, but setting this to true denies showing the 'image'
              color: new Color("green"),
              image: "https://images-na.ssl-images-amazon.com/images/I/61mx-VbrS0L.jpg",
              thumbnail: "https://2.bp.blogspot.com/-H_SZ3nAmNsI/VrJeARpbuSI/AAAAAAAABfc/szsV7_F609k/s200/emoji.jpg",
              forceShowWhenInForeground: true,
              channel: "vue-channel",
              ticker: "Special ticker text for Vue (Android only)",
              at: new Date(new Date().getTime() + (0 * 1000)), // 5 seconds from now
              actions: [
                {
                  id: "yes",
                  type: "button",
                  title: "Yes (and launch app)",
                  launch: true
                },
                {
                  id: "no",
                  type: "button",
                  title: "No",
                  launch: false
                }
              ]
            },
            {
              id: 2,
              title: 'X2?',
              subtitle: 'This poster is awesome!',
              body: 'The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app.',
              bigTextStyle: false, // Allow more than 1 row of the 'body' text on Android, but setting this to true denies showing the 'image'
              color: new Color("green"),
              image: "https://images-na.ssl-images-amazon.com/images/I/61mx-VbrS0L.jpg",
              thumbnail: "https://2.bp.blogspot.com/-H_SZ3nAmNsI/VrJeARpbuSI/AAAAAAAABfc/szsV7_F609k/s200/emoji.jpg",
              forceShowWhenInForeground: true,
              channel: "vue-channel",
              ticker: "Special ticker text for Vue (Android only)",
              at: new Date(new Date().getTime() + (0 * 1000)), // 5 seconds from now
              actions: [
                {
                  id: "yes",
                  type: "button",
                  title: "Yes (and launch app)",
                  launch: true
                },
                {
                  id: "no",
                  type: "button",
                  title: "No",
                  launch: false
                }
              ]
            },

            {
              id: 3,
              title: 'X3?',
              subtitle: 'This poster is awesome!',
              body: 'The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app.',
              bigTextStyle: false, // Allow more than 1 row of the 'body' text on Android, but setting this to true denies showing the 'image'
              color: new Color("green"),
              image: "https://images-na.ssl-images-amazon.com/images/I/61mx-VbrS0L.jpg",
              thumbnail: "https://2.bp.blogspot.com/-H_SZ3nAmNsI/VrJeARpbuSI/AAAAAAAABfc/szsV7_F609k/s200/emoji.jpg",
              forceShowWhenInForeground: true,
              channel: "vue-channel",
              ticker: "Special ticker text for Vue (Android only)",
              at: new Date(new Date().getTime() + (0 * 1000)), // 5 seconds from now
              actions: [
                {
                  id: "yes",
                  type: "button",
                  title: "Yes (and launch app)",
                  launch: true
                },
                {
                  id: "no",
                  type: "button",
                  title: "No",
                  launch: false
                }
              ]
            },
            {
            id: 4,
              title: 'X4?',
              subtitle: 'This poster is awesome!',
              body: 'The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app. The big brown Vue app jumped over the lazy Angular app.',
              bigTextStyle: false, // Allow more than 1 row of the 'body' text on Android, but setting this to true denies showing the 'image'
              color: new Color("green"),
              image: "https://images-na.ssl-images-amazon.com/images/I/61mx-VbrS0L.jpg",
              thumbnail: "https://2.bp.blogspot.com/-H_SZ3nAmNsI/VrJeARpbuSI/AAAAAAAABfc/szsV7_F609k/s200/emoji.jpg",
              forceShowWhenInForeground: true,
              channel: "vue-channel",
              ticker: "Special ticker text for Vue (Android only)",
              at: new Date(new Date().getTime() + (0 * 1000)), // 5 seconds from now
              actions: [
                {
                  id: "yes",
                  type: "button",
                  title: "Yes (and launch app)",
                  launch: true
                },
                {
                  id: "no",
                  type: "button",
                  title: "No",
                  launch: false
                }
              ]
            }



            ]
      }
    },

    methods: {



      onTapHasPermission() {
        LocalNotifications.hasPermission()
            .then(granted => {
              alert({
                title: "Permission granted?",
                message: granted ? "YES" : "NO",
                okButtonText: "OK"
              });
            });
      },

      shuffleArray(array) {
        //let prayers = this.prayers.length; 

        let counter = this.prayers.length;


        while(counter > 0) {
         
          let index = Math.floor(Math.random() * counter); 


          counter--;

          let temp = array[counter];
          array[counter] = array[index];
          array[index] = temp;
        }

        // return array;
        this.increaseSecForEach(array);
      },

      increaseSecForEach(array) {
        // var prayers = this.shuffleArray(this.prayers);
        // var seconds = 5;
        // for(let i=0; i<this.alertNumber; i++) {
        //   this.localPrayers.push(prayers[i]);
        //   // this.localPrayers[i].at = new Date(new Date().getTime() + (seconds * 1000));
        //   // seconds++;
        // }
        
        let sec=5;
        for(let i=0; i<this.alertNumber; i++) {          
          array[i]['at'] = new Date(new Date().getTime() + (sec * 1000));
          this.localPrayers.push(array[i]);
          sec+=5;
        }

        /*for(let i=0; i<this.localPrayers.length; i++) {
          
          alert(this.localPrayers[0]);
        }*/

        // return this.localPrayers;


      }, 


      onTapScheduleNotification() {
        var index = 1;
       

        /*$.each(this.prayers, function(elem) {
          if(localPrayers.length() <= this.alertNumber) {
            localPrayers.push(elem);
          }
        });*/


       this.shuffleArray(this.prayers);

        //alert(JSON.stringify(this.shuffleArray(this.prayers)));
      


        LocalNotifications.schedule(
             this.localPrayers 
            )
            .then(() => {
              alert({
                title: "Notification scheduled",
                message: "ID: 1",
                okButtonText: "OK, thanks"
              });
            })
            .catch(error => console.log("doSchedule error: " + error));
      },

      onTapCancelAll() {
        LocalNotifications.cancelAll()
            .then(() => {
              alert({
                title: "All canceled",
                okButtonText: "Awesome!"
              });
            })
            .catch(error => console.log("doCancelAll error: " + error));
      }
    }
  }
</script>

<style scoped>
  ActionBar {
    background-color: #53ba82;
    color: #ffffff;
  }

  .message {
    font-size: 14;
    margin: 16;
    color: #53ba82;
  }

  Button.btn {
    font-size: 14;
    border-radius: 3;
    border-width: 2;
    border-color: #63d4a5;
    color: #63d4a5;
    padding: 12;
    margin: 16;
  }
</style>
