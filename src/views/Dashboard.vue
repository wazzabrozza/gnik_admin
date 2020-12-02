<template>
  <div class="d-flex">
    <sidebar @menu="menuChange"></sidebar>
    <v-container class="col-7" fluid>
      <div class="dashboard-page">
        <v-row>
          <div v-if="this.menu === 1" style="width: 100%">
            <v-row no-gutters class="d-flex justify-space-between mt-10 mb-6">
          <h1 class="page-title">Review Products</h1>
        </v-row>
            <reviewProducts
              :headers="approveHeaders"
              :catalogueItems="reviewCatalogueItems"
            ></reviewProducts>
            <div class="d-flex">
              <v-btn class="mt-5 mr-3 ml-auto" depressed color="primary"
                >Add To Catalogue</v-btn
              >
              <v-btn class="mt-5" depressed color="error"
                >Reject For Review</v-btn
              >
            </div>
          </div>
          <div v-else style="width: 100%">
                 <v-tabs
      color="deep-purple accent-4"
      right
      class="mt-10"
    >
            <v-row no-gutters class="d-flex justify-space-between mb-6">
          <h1 class="page-title" style="color:black;">Catalogue Products</h1>
          <div class="d-flex">
            <v-tab>Active</v-tab>
      <v-tab>Archived</v-tab>
          </div>
        </v-row>
      <v-tab-item class="pt-5">
            <uploadItems
              :headers="headers"
              :catalogueItems="catalogueItems"
            ></uploadItems>
      </v-tab-item>
      <v-tab-item class="pt-5">
        <archived
         :headers="headers"
        :catalogueItems="archivedCatalogueItems"
        >
        </archived>
      </v-tab-item>
              </v-tabs>
          </div>
        </v-row>
      </div>
    </v-container>
  </div>
</template>

<script>
import sidebar from '../components/SideBar'
import reviewProducts from '../components/ReviewProducts'
import uploadItems from '../components/UploadItems'
import archived from '../components/ArchivedProducts'
export default {
  name: 'Dashboard',
  components: {
    sidebar,
    reviewProducts,
    uploadItems,
    archived
  },
  data () {
    return {
      menu: 0,
      detailedInfoDialog: false,
      dialogDelete: false,
      productsDialog: false,
      approveHeaders: [
        {
          text: 'Product',
          align: 'start',
          sortable: false,
          value: 'title'
        },
        { text: 'Category', value: 'category' },
        { text: 'Sub Category', value: 'subCategory' },
        { text: 'Style Code', value: 'styleCode' },
        { text: 'Stock (USD)', value: 'price1' },
        { text: 'Repeat Order (USD)', value: 'price2' },
        { text: 'Details', value: 'actions', sortable: false }
      ],
      headers: [
        {
          text: 'Product',
          align: 'start',
          sortable: false,
          value: 'title'
        },
        { text: 'Category', value: 'category' },
        { text: 'Sub Category', value: 'subCategory' },
        { text: 'Style Code', value: 'styleCode' },
        { text: 'Stock (USD)', value: 'price1' },
        { text: 'Repeat Order (USD)', value: 'price2' },
        { text: 'Status', value: 'status' },
        { text: 'Details', value: 'actions', sortable: false },
        { text: 'Actions', value: 'crud', sortable: false }
      ],
      reviewCatalogueItems: [
        {
          id: 4,
          title: 'Iron bowl',
          category: 'Hard Goods',
          subCategory: 'Table Top',
          categoryId: 5,
          subCategoryId: 32,
          styleCode: 'RST-STOCK',
          price1: '2.50',
          price2: '3.38',
          quantity: '10,000',
          finish: 'Mint Green',
          maxExFactory: '22 to 30 days',
          lables: 'Can be done',
          fitForSale: 'Yes',
          repeatOrders: 'Yes',
          expansion: [
            {
              title: 'Sizing Parameters',
              children: [
                { title: 'Size (cm)', value: '15x15x7' },
                { title: 'Inner Dimensions (cm)', value: '17.5X17.5X8.5' },
                { title: 'Piece Packing Weight', value: '0.37' }
              ]
            },
            {
              title: 'Repeat Order Information',
              children: [
                { title: 'Lead Time (Ex-India - Days)', value: '45' },
                { title: 'Repeat Order MOQ', value: '500' }
              ]
            },
            {
              title: 'Additional Information',
              children: [
                {
                  title: 'Payment Terms',
                  value:
                    '50% advance after initial inspection and balance after Final inspection'
                }
              ]
            }
          ],
          image:
            'https://drive.google.com/file/d/1JRSjseAq-REKWSXdnrrP8ehpQDsCakLD/preview',
          status: 'Waiting Approval'
        },
        {
          id: 5,
          title: 'Silk Check Cushion Cover',
          category: 'Home Furnishing',
          subCategory: 'Decoration',
          categoryId: 4,
          subCategoryId: 17,
          styleCode: 'Silk',
          price1: '4.35',
          price2: '9.11',
          quantity: '50 Assorted',
          finish: 'N/A',
          maxExFactory: '5 to 7 days',
          lables: 'Can be done',
          fitForSale: 'Yes',
          repeatOrders: 'Yes',
          expansion: [
            {
              title: 'Sizing Parameters',
              children: [
                { title: 'Size (cm)', value: '40x40' },
                { title: 'Inner Dimensions (cm)', value: '50x50x40' },
                { title: 'Piece Packing Weight', value: '10' }
              ]
            },
            {
              title: 'Repeat Order Information',
              children: [
                { title: 'Lead Time (Ex-India - Days)', value: '120' },
                { title: 'Repeat Order MOQ', value: '300' }
              ]
            },
            {
              title: 'Additional Information',
              children: [
                {
                  title: 'Payment Terms',
                  value:
                    '50% advance after initial inspection and balance after Final inspection'
                }
              ]
            }
          ],
          image:
            'https://drive.google.com/file/d/1-M1MVlEdLLKBlmWzLhmX192yF7AD-uSb/preview',
          status: 'Waiting Approval'
        }
      ],
      catalogueItems: [
        {
          id: 1,
          title: 'Braided Round Rugs',
          categoryId: 3,
          subCategoryId: 18,
          category: 'Home Furnishing',
          subCategory: 'Floor Covering',
          styleCode: 'DI/RG/4700',
          price1: '7.45',
          price2: '8.05',
          image:
            'https://drive.google.com/file/d/10wP91npAFp026qd3PjI7zsQiEuwveOi7/preview',
          status: 'Active'
        },
        {
          id: 2,
          title: 'Plated Lamp Shades',
          categoryId: 4,
          subCategoryId: 22,
          category: 'Hard Goods',
          subCategory: 'Lights',
          styleCode: 'Lamp Shades',
          price1: '16.88',
          price2: '20.25',
          quantity: 'N/A',
          finish: 'N/A',
          maxExFactory: '16 to 21 days',
          lables: 'Can be done',
          fitForSale: 'Yes',
          repeatOrders: 'Yes',
          expansion: [
            {
              title: 'Sizing Parameters',
              children: [
                { title: 'Size (inch)', value: 'N/A' },
                { title: 'Inner Dimensions (inch)', value: '20' },
                { title: 'Piece Packing Weight', value: '7.5' }
              ]
            },
            {
              title: 'Repeat Order Information',
              children: [
                { title: 'Lead Time (Ex-India - Days)', value: '75' },
                { title: 'Repeat Order MOQ', value: '300' }
              ]
            },
            {
              title: 'Additional Information',
              children: [
                {
                  title: 'Payment Terms',
                  value:
                    '50% advance after initial inspection and balance after Final inspection'
                }
              ]
            }
          ],
          image:
            'https://drive.google.com/file/d/1fI1E7D7MW_L58GASHXCqRJ2ytN3tJi5b/preview',
          status: 'Active'
        },
        {
          id: 3,
          title: 'Tray Set of 3',
          categoryId: 3,
          subCategoryId: 15,
          category: 'Hard Goods',
          subCategory: 'Kitchen and Dining',
          styleCode: '266417',
          price1: '52.90',
          price2: '63.06',
          quantity: '150',
          finish: 'N/A',
          maxExFactory: '22 to 30 days',
          lables: 'Can be done',
          fitForSale: 'Yes',
          repeatOrders: 'Yes',
          expansion: [
            {
              title: 'Sizing Parameters',
              children: [
                { title: 'Size (inch)', value: '25.5' },
                { title: 'Inner Dimensions (inch)', value: '26.5x18x4.5' },
                { title: 'Piece Packing Weight', value: '1' }
              ]
            },
            {
              title: 'Repeat Order Information',
              children: [
                { title: 'Lead Time (Ex-India - Days)', value: '75' },
                { title: 'Repeat Order MOQ', value: '300' }
              ]
            },
            {
              title: 'Additional Information',
              children: [
                {
                  title: 'Payment Terms',
                  value:
                    '50% advance after initial inspection and balance after Final inspection'
                }
              ]
            }
          ],
          image:
            'https://drive.google.com/file/d/1iP4WeAYB7OElSIl5SWiygL9pFagiCOut/preview',
          status: 'Active'
        }
      ],
      archivedCatalogueItems: [
        {
          id: 2,
          title: 'Plated Lamp Shades',
          categoryId: 4,
          subCategoryId: 22,
          category: 'Hard Goods',
          subCategory: 'Lights',
          styleCode: 'Lamp Shades',
          price1: '16.88',
          price2: '20.25',
          quantity: 'N/A',
          finish: 'N/A',
          maxExFactory: '16 to 21 days',
          lables: 'Can be done',
          fitForSale: 'Yes',
          repeatOrders: 'Yes',
          expansion: [
            {
              title: 'Sizing Parameters',
              children: [
                { title: 'Size (inch)', value: 'N/A' },
                { title: 'Inner Dimensions (inch)', value: '20' },
                { title: 'Piece Packing Weight', value: '7.5' }
              ]
            },
            {
              title: 'Repeat Order Information',
              children: [
                { title: 'Lead Time (Ex-India - Days)', value: '75' },
                { title: 'Repeat Order MOQ', value: '300' }
              ]
            },
            {
              title: 'Additional Information',
              children: [
                {
                  title: 'Payment Terms',
                  value:
                    '50% advance after initial inspection and balance after Final inspection'
                }
              ]
            }
          ],
          image:
            'https://drive.google.com/file/d/1fI1E7D7MW_L58GASHXCqRJ2ytN3tJi5b/preview',
          status: 'Archived'
        }
      ]
    }
  },
  computed: {
    formTitle () {
      return this.menu === 1 ? 'Review Products' : 'Catalogue Products'
    }
  },

  methods: {
    menuChange: function (value) {
      this.menu = value
    }
  }
}
</script>
