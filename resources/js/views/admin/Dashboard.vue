<template>
  <div v-cloak class="dashboard-page">
    <a class="btn purple negative upload-btn" href="" @click.prevent="$router.push('/admin/image-upload')">Upload Images</a>
    <edit-modal ref="editModal" :creator="creator"></edit-modal>
    <media-modal ref="mediaModal" :username="creator? creator.username : ''" ></media-modal>
    <products-modal v-if="$root.isMobile" ref="productsModal" ></products-modal>
    <modal class="download-modal" width="860px" height="auto" name="downloadModal">
      <a class="close" @click.prevent="$modal.hide('downloadModal')">
        <svg xmlns="http://www.w3.org/2000/svg" class="icon" style="width: 20px; height: 20px;vertical-align: middle;fill: currentColor;overflow: hidden;" viewBox="0 0 1024 1024" version="1.1">
          <path
          d="M998.733 930.989l-410.781-410.783 410.77-410.771c0.005-0.005 0.010-0.007 0.016-0.014 21.271-21.272 21.271-55.755 0.001-77.022-21.269-21.269-55.753-21.269-77.022 0.002-0.005 0.004-0.010 0.010-0.015 0.017l-0.002-0.003-410.769 410.77-410.771-410.767c-0.005-0.006-0.010-0.013-0.015-0.017-21.27-21.271-55.755-21.271-77.024-0.002-21.267 21.267-21.27 55.75 0.001 77.022 0.006 0.006 0.011 0.009 0.016 0.014v0.003l410.769 410.768-410.781 410.783c-0.001 0.003-0.002 0.003-0.002 0.003-21.27 21.269-21.27 55.752 0 77.022 21.266 21.265 55.752 21.265 77.020 0 0.001-0.002 0.002-0.002 0.002-0.002l410.783-410.782 410.782 410.782c0 0 0.002 0 0.003 0.002 21.268 21.265 55.753 21.265 77.020 0 21.272-21.27 21.272-55.753 0-77.022 0.001 0 0 0-0.002-0.003z" />
        </svg>
      </a>
      <img :src="$root.storageUrl+'/images/artigram-logo.png'"/>
      <div class="title"><svg viewBox="0 0 128 128" xmlns="http://www.w3.org/2000/svg"><title/><g data-name="Confetti" id="f3d8523b-b79d-41af-bbaa-11221b3a2a9b"><path d="M82.13,85.05c-.8.8-2.95.11-5.94-1.7-4.34-2.63-10.44-7.62-16.69-13.86S48.28,57.15,45.65,52.81c-1.8-3-2.5-5.14-1.7-5.94,2-2,12.08,5,22.63,15.56S84.09,83.1,82.13,85.05Z" fill="#fe852b"/><path d="M76.19,83.35c-4.34-2.63-10.44-7.62-16.69-13.86S48.28,57.15,45.65,52.81C50,55.44,56.09,60.42,62.33,66.67S73.56,79,76.19,83.35Z" fill="#d46f24"/><path d="M81.6,85.33l-8.73,4.54-7.3,3.8-4.82,2.51-7.11,3.7-4.82,2.52L41.91,106l-4.79,2.49L30.32,112l-4.75,2.47L18.9,118l-.69.36a6.13,6.13,0,0,1-3.74.62A6.09,6.09,0,0,1,10,110l.38-.72L14,102.68,16.51,98l3.64-6.77,2.55-4.74,3.71-6.92L29,74.78l3.8-7.07L35.31,63l3.9-7.25,4.47-8.33c-.73,2.81,6,12.28,15.83,22.12S78.76,86,81.6,85.33Z" fill="#fe9f59"/><path d="M60.76,96.18l-7.11,3.7a93.63,93.63,0,0,1-17-15.12,94,94,0,0,1-7.69-10l3.8-7.07a87,87,0,0,0,28,28.47Z" fill="#a54fe7"/><path d="M48.84,102.4,41.91,106A93.74,93.74,0,0,1,30.64,96a92.9,92.9,0,0,1-7.94-9.5l3.71-6.92a87.25,87.25,0,0,0,7.73,9.89A86.74,86.74,0,0,0,48.84,102.4Z" fill="#a54fe7"/><path d="M37.11,108.49,30.32,112q-2.91-2.4-5.61-5a93.65,93.65,0,0,1-8.19-9l3.64-6.77a87.89,87.89,0,0,0,17,17.3Z" fill="#a54fe7"/><path d="M25.57,114.51,18.9,118l-.06-.06a89.58,89.58,0,0,1-8.43-8.6L14,102.68a84.72,84.72,0,0,0,8.27,8.88C23.34,112.58,24.43,113.56,25.57,114.51Z" fill="#a54fe7"/><path d="M72.88,89.87l-7.3,3.8A94,94,0,0,1,42.73,73.45,94.36,94.36,0,0,1,35.31,63l3.9-7.25a87.37,87.37,0,0,0,7.13,11A87.13,87.13,0,0,0,72.88,89.87Z" fill="#a54fe7"/><path d="M22.26,111.56c1.07,1,2.17,2,3.3,2.95L18.9,118l-.06-.06.06-.11Z" fill="#9831e7"/><path d="M28.17,100.56a85,85,0,0,0,8.94,7.93L30.32,112q-2.91-2.4-5.61-5l.3-.55Z" fill="#9831e7"/><path d="M48.84,102.4,41.91,106A93.74,93.74,0,0,1,30.64,96l.54-1,2.95-5.51A86.74,86.74,0,0,0,48.84,102.4Z" fill="#9831e7"/><path d="M60.76,96.18l-7.11,3.7a93.63,93.63,0,0,1-17-15.12l.8-1.49,2.76-5.12A86.72,86.72,0,0,0,60.76,96.18Z" fill="#9831e7"/><path d="M72.88,89.87l-7.3,3.8A94,94,0,0,1,42.73,73.45l1.07-2,2.55-4.74A87.13,87.13,0,0,0,72.88,89.87Z" fill="#9831e7"/><path d="M76.5,64.5s13.45-25.56,28-18c13.86,7.2,5.32,18.7,5.32,18.7" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><path d="M67.5,51.5S89.93,40.83,82.37,26.27C75.17,12.41,63.68,21,63.68,21" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><path d="M64.5,65.5,100,29a12.73,12.73,0,0,0,0-18h0" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><polygon fill="#fe9f59" points="49.5 27.6 50.58 29.79 53 30.14 51.25 31.85 51.66 34.26 49.5 33.12 47.34 34.26 47.75 31.85 46 30.14 48.42 29.79 49.5 27.6"/><polygon fill="#fe5959" points="92.48 7.25 92.05 9.66 93.78 11.38 91.36 11.71 90.26 13.89 89.19 11.69 86.78 11.32 88.55 9.63 88.16 7.21 90.31 8.37 92.48 7.25"/><polygon fill="#fe5959" points="100.48 58.26 100.05 60.66 101.78 62.38 99.36 62.71 98.26 64.89 97.19 62.69 94.78 62.32 96.55 60.63 96.16 58.21 98.31 59.37 100.48 58.26"/><path d="M81,72s17.5-3.5,18.5,8.5S89,91,89,91" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><circle cx="72.5" cy="30.5" fill="#fe5959" r="2"/><circle cx="108" cy="41" fill="#fe5959" r="2"/><circle cx="111" cy="12" fill="#a54fe7" r="2"/></g></svg>Let us help you boost your first store<svg viewBox="0 0 128 128" xmlns="http://www.w3.org/2000/svg"><title/><g data-name="Confetti" id="f3d8523b-b79d-41af-bbaa-11221b3a2a9b"><path d="M82.13,85.05c-.8.8-2.95.11-5.94-1.7-4.34-2.63-10.44-7.62-16.69-13.86S48.28,57.15,45.65,52.81c-1.8-3-2.5-5.14-1.7-5.94,2-2,12.08,5,22.63,15.56S84.09,83.1,82.13,85.05Z" fill="#fe852b"/><path d="M76.19,83.35c-4.34-2.63-10.44-7.62-16.69-13.86S48.28,57.15,45.65,52.81C50,55.44,56.09,60.42,62.33,66.67S73.56,79,76.19,83.35Z" fill="#d46f24"/><path d="M81.6,85.33l-8.73,4.54-7.3,3.8-4.82,2.51-7.11,3.7-4.82,2.52L41.91,106l-4.79,2.49L30.32,112l-4.75,2.47L18.9,118l-.69.36a6.13,6.13,0,0,1-3.74.62A6.09,6.09,0,0,1,10,110l.38-.72L14,102.68,16.51,98l3.64-6.77,2.55-4.74,3.71-6.92L29,74.78l3.8-7.07L35.31,63l3.9-7.25,4.47-8.33c-.73,2.81,6,12.28,15.83,22.12S78.76,86,81.6,85.33Z" fill="#fe9f59"/><path d="M60.76,96.18l-7.11,3.7a93.63,93.63,0,0,1-17-15.12,94,94,0,0,1-7.69-10l3.8-7.07a87,87,0,0,0,28,28.47Z" fill="#a54fe7"/><path d="M48.84,102.4,41.91,106A93.74,93.74,0,0,1,30.64,96a92.9,92.9,0,0,1-7.94-9.5l3.71-6.92a87.25,87.25,0,0,0,7.73,9.89A86.74,86.74,0,0,0,48.84,102.4Z" fill="#a54fe7"/><path d="M37.11,108.49,30.32,112q-2.91-2.4-5.61-5a93.65,93.65,0,0,1-8.19-9l3.64-6.77a87.89,87.89,0,0,0,17,17.3Z" fill="#a54fe7"/><path d="M25.57,114.51,18.9,118l-.06-.06a89.58,89.58,0,0,1-8.43-8.6L14,102.68a84.72,84.72,0,0,0,8.27,8.88C23.34,112.58,24.43,113.56,25.57,114.51Z" fill="#a54fe7"/><path d="M72.88,89.87l-7.3,3.8A94,94,0,0,1,42.73,73.45,94.36,94.36,0,0,1,35.31,63l3.9-7.25a87.37,87.37,0,0,0,7.13,11A87.13,87.13,0,0,0,72.88,89.87Z" fill="#a54fe7"/><path d="M22.26,111.56c1.07,1,2.17,2,3.3,2.95L18.9,118l-.06-.06.06-.11Z" fill="#9831e7"/><path d="M28.17,100.56a85,85,0,0,0,8.94,7.93L30.32,112q-2.91-2.4-5.61-5l.3-.55Z" fill="#9831e7"/><path d="M48.84,102.4,41.91,106A93.74,93.74,0,0,1,30.64,96l.54-1,2.95-5.51A86.74,86.74,0,0,0,48.84,102.4Z" fill="#9831e7"/><path d="M60.76,96.18l-7.11,3.7a93.63,93.63,0,0,1-17-15.12l.8-1.49,2.76-5.12A86.72,86.72,0,0,0,60.76,96.18Z" fill="#9831e7"/><path d="M72.88,89.87l-7.3,3.8A94,94,0,0,1,42.73,73.45l1.07-2,2.55-4.74A87.13,87.13,0,0,0,72.88,89.87Z" fill="#9831e7"/><path d="M76.5,64.5s13.45-25.56,28-18c13.86,7.2,5.32,18.7,5.32,18.7" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><path d="M67.5,51.5S89.93,40.83,82.37,26.27C75.17,12.41,63.68,21,63.68,21" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><path d="M64.5,65.5,100,29a12.73,12.73,0,0,0,0-18h0" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><polygon fill="#fe9f59" points="49.5 27.6 50.58 29.79 53 30.14 51.25 31.85 51.66 34.26 49.5 33.12 47.34 34.26 47.75 31.85 46 30.14 48.42 29.79 49.5 27.6"/><polygon fill="#fe5959" points="92.48 7.25 92.05 9.66 93.78 11.38 91.36 11.71 90.26 13.89 89.19 11.69 86.78 11.32 88.55 9.63 88.16 7.21 90.31 8.37 92.48 7.25"/><polygon fill="#fe5959" points="100.48 58.26 100.05 60.66 101.78 62.38 99.36 62.71 98.26 64.89 97.19 62.69 94.78 62.32 96.55 60.63 96.16 58.21 98.31 59.37 100.48 58.26"/><path d="M81,72s17.5-3.5,18.5,8.5S89,91,89,91" fill="none" stroke="#9831e7" stroke-linecap="round" stroke-linejoin="round" stroke-width="3"/><circle cx="72.5" cy="30.5" fill="#fe5959" r="2"/><circle cx="108" cy="41" fill="#fe5959" r="2"/><circle cx="111" cy="12" fill="#a54fe7" r="2"/></g></svg></div>
      <div class="txt-content">Here is a little gift from us to help you earn money with Artigram!
        Click the attached link and download your gift $100 worth of photos licensed for commercial use in your Artigram store!</div>
        <div class="btn-box"><a class="btn purple" href="https://ondema.s3-eu-west-1.amazonaws.com/GIVEAWAY+IMAGES/Giveaway+content.zip">Download</a></div>
        <div class="btn-2-box"><a href="https://sell.support.artigram.me/article/326-artigram-gift-image-terms-of-use ">Gift terms of use</a></div>
      </modal>
      <div style="" class="profile-page">
        <div>
          <div class="container no-padding">
              <div class="" style="">
                <account-gallery :render="$root.renderGallery" :user="user" :creator="creator" ref="approvedGallery"  status="approved" limit="12" :per-page="12" is-first-time="1"></account-gallery>
              </div>
              <div class="" style="">
                <account-gallery :render="$root.renderGallery" :user="user" :creator="creator" status="pending" limit="4" :per-page="4"  is-first-time="0"></account-gallery>
              </div>
              <div class="" style="">
                <account-gallery :render="$root.renderGallery" :user="user" :creator="creator" status="not approved" limit="4" :per-page="4"  is-first-time="0"></account-gallery>
              </div>
            </div>
          </div>
        </div>
      </div>
    </template>

    <script>
    import Api from "../../apis/Api";
    export default {
      props:['creator','user'],
      data() {
        return {
          bio: '',
        };
      },
      watch: {
        creator(val) {
          this.bio=this.creator.bio;
        },
        '$route': {
          handler: function() {
          },
          deep: true,
          immediate: true
        }
      },
      methods:{
        goShop() {
          this.$router.push('/@'+this.creator.username);
        },
        openBioModal() {
          this.$refs.bio.focus();
        },
        closeBioModal() {
          this.bio = $('.bio').data('bio');
        },
        updateBio() {
          this.$ma.trackEvent({
            action: 'account-page',
            properties: {
              feature: 'edit bio',
              type: 'text-enterd',
            },
          });
          var formData = new FormData();
          formData.append('bio', this.bio);
          formData.append('creatorId', this.creator.id);
          Api.post('/api/set-bio', formData)
          .then(response => {
            $('.bio').data('bio', this.bio);
            this.$modal.hide('bioModal');
          });
        },
      },
      created() {
      },
      mounted() {
      }
    };
    </script>
