<template>
  <form id="form" @submit.prevent="onSubmit">
    <TabWrapper>
      <Tab :selected="true">
         <h4 class="text-2xl">
          Share your work with us
        </h4>
        <p class="mt-3 mb-3">
          To ensure the the quality of our marketplace, we limit our seller community to the most qualified creators. Let our curators know why you’d be a great seller:
        </p>
        <div class="flex flex-row input-row">
          <Input
            name="firstName"
            label="First Name"
            type="text"
            col="6"
          />
          <Input
            name="lastName"
            label="Last Name"
            type="text"
            col="6"
          />
        </div>
        <SelectGroup
          selectId="shopCategory"
          label="Your Shop Category"
          placeholder="Select Category"
          ref="categorySelected"
          :options="categoryOptions"
        />
        <Input
          name="portfolioLink"
          label="Porfolio Link"
          type="text"
          :confirmContent="true"
          col="12"
        />
        <RadioGroup
          name="onlineStore"
          message="Do you already have an online store?"
          :radioList="radioList"
        />
        <Input
          name="onlineStoresISellToday"
          label="Online stores I sell on today"
          placeholder="Enter urls"
          type="textarea"
          col="12"
        />
      </Tab>
      <Tab>
        <h4 class="text-2xl">
          Tell us a little about yourself
        </h4>
        <p class="mt-3 mb-3">
          Your answers will help us provide you with a more personalized experience as a seller!
        </p>
        <SelectGroup 
          selectId="qualityQuestion"
          label="When creating products, which best describes your perspective on quality?"
          placeholder="Select Answer"
          ref="qualitySelected"
          :options="qualityOptions"
        />
        <SelectGroup 
          selectId="onlineSellerQuestion"
          label="How would you describe your experience level as an online seller?"
          placeholder="Select Answer"
          ref="onlineSelected"
          :options="onlineOptions"
        />
        <SelectGroup 
          selectId="businessMarketingQuestion"
          label="How would you describe your understanding of business and marketing?"
          placeholder="Select Answer"
          ref="businessSelected"
          :options="businessOptions"
        />
      </Tab>
    </TabWrapper>
  </form>
</template>

<script>
import Airtable from 'airtable';
import { AIRTABLE_API_KEY } from '../env';
const base = new Airtable({apiKey: AIRTABLE_API_KEY}).base('appyAikWHmqPVkRsd');

export default {
  data() {
    return {
      radioList: [ 'Yes', 'No' ],
      categoryOptions: ['Graphics', 'Fonts', 'Templates', 'Add-ons', 'Photos', 'Web Themes', '3D'],
      qualityOptions: [
        'I don’t care what it takes, my products are the highest quality possible',
        'I put in enough effort to make my product pretty high quality, but at some point my time is better spent elsewhere',
        'I try to get quality products out quickly, even if I need to take a shortcut now and then',
        'I spend the minimum amount of time & effort it takes to create products that are acceptable quality.',
        'Quantity is more important to me than quality.'
      ],
      onlineOptions: [
        'I sell on multiple marketplaces and through my own website',
        'I have experience selling through only my own website',
        'I have experience selling through multiple marketplaces',
        'I have experience selling through one online marketplace',
        'I’m new to selling creative products online'
      ],
      businessOptions: [
        'I have an extensive background in business and/or marketing',
        'I’m familiar with some skills & techniques, but I’m not sure how to apply them when selling my creative work',
        'I’m vaguely aware of basic business & marketing concepts',
        'I’m not interested in understanding business & marketing'
      ],
    }
  },
  methods: {
    onSubmit(e) {
      base('Sellers').create([
        {
          'fields': {
            firstName: e.target.elements.firstName.value,
            lastName: e.target.elements.lastName.value,
            shopCategory: this.$refs.categorySelected.$el.children[1].children[0].children[0].children[0].innerText,
            portfolioLink: e.target.elements.portfolioLink.value,
            onlineStore: e.target.elements.onlineStore.value,
            onlineStoresISellToday: e.target.elements.onlineStoresISellToday.value,
            qualityQuestion: this.$refs.qualitySelected.$el.children[1].children[0].children[0].children[0].innerText,
            onlineSellerQuestion: this.$refs.onlineSelected.$el.children[1].children[0].children[0].children[0].innerText,
            businessMarketingQuestion: this.$refs.businessSelected.$el.children[1].children[0].children[0].children[0].innerText
          }
        }
      ], (err, records) => {
        if(err) {
          console.error(err);
          return;
        }
        records.forEach(record => {
          console.log(record.getId())
        });
      });
    }
  }
}
</script>

<style lang="scss" scoped>
.input-row {
  .input-field {
    &:first-of-type {
      padding-right: 9px;
      @media only screen and (min-width: 768px) {
        padding-right: 11px;
      }
    }
    &:nth-of-type(2) {
      padding-left: 9px;
      @media only screen and (min-width: 768px) {
        padding-left: 11px;
      }
    }
  }
}
</style>