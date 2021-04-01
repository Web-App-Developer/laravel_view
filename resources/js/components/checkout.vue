<template>
  <div class="checkout-main-box">
    <div class="checkout-product-card">
      <div class="checkout-heading-box">
        <h6>Order Summary Quick View</h6>
        <a href="#">View Details</a>
      </div>

      <div class="checkout-table-list">
        <div class="checkout-price-title">
          <h6>Total Cost</h6>
          <h6>Total Shipping</h6>
          <h6>Total Discount</h6>
          <h6 class="total-price">Order Sub Total</h6>
        </div>
        <div class="checkout-price-box">
          <h6>$23.61 USD</h6>
          <h6>$3.99 USD</h6>
          <h6>$4.17 USD</h6>
          <h6 class="total-price">$23.79 USD</h6>
        </div>
      </div>
    </div>

    <div class="shipping-details-box">
      <h5>Shipping Details</h5>
      <form class="row no-gutters">
        <div class="col-12">
          <div class="form-group p-1">
            <input
              class="form-control"
              placeholder="Email Address"
              type="text"
            />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <input class="form-control" placeholder="First name" type="text" />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <input class="form-control" placeholder="Last name" type="text" />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1">
            <input
              class="form-control"
              placeholder="Street Address"
              type="text"
            />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1">
            <input
              class="form-control"
              placeholder="Apartment, Suit, Unit etc"
              type="text"
            />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <input class="form-control" placeholder="Town/City" type="text" />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <select class="form-control">
              <option></option>
            </select>
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <select class="form-control">
              <option>United States</option>
            </select>
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <input
              class="form-control"
              placeholder="Postcode / ZIP"
              type="text"
            />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1 card-box">
            <div>
              <label class="radio-container"
                >Credit Cards
                <input type="radio" checked="checked" name="radio" />
                <span class="checkmark"></span>
              </label>
            </div>
            <img :src="image" class="card-image img-fluid" />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1">
            <label for="name">Name on Card</label>
            <input class="form-control" placeholder="Fullname" type="text" />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1">
            <label for="name">Card Number</label>
            <input class="form-control" placeholder="" type="text" />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <label for="name">Exp. Date</label>
            <input class="form-control" placeholder="" type="text" />
          </div>
        </div>

        <div class="col-6">
          <div class="form-group p-1">
            <label for="name">Security Code</label>
            <input class="form-control" placeholder="" type="text" />
          </div>
        </div>
        <div class="col-12">
          <div class="form-group p-1 card-box">
            <div>
              <label class="radio-container"
                >Paypal
                <input type="radio" name="radio" />
                <span class="checkmark"></span>
              </label>
            </div>
            <img :src="paypal" class="paypal-image img-fluid" />
          </div>
        </div>

        <div class="col-12">
          <div class="form-group p-1">
            <div class="btn btn-block purple">Place order</div>
          </div>
        </div>
      </form>

      <div class="checkout-details-summary mt-4">
        <h4>Order Summary</h4>
        <hr />
        <div class="summary-content">
          <div class="order-product-box">
            <img :src="tshirt" class="product-image img-fluid" />
          </div>
          <div class="checkout-pricing-box">
            <div class="checkout-pricing-heading-view">
              <h5>Tshirt-Anvil-980</h5>
              <h5>1x $27.99 USD</h5>
            </div>

            <div class="checkout-pricing-text">
              <h6>size: S</h6>
              <h6></h6>
            </div>

            <div class="checkout-pricing-text">
              <h6 class="text-light-grey">Shipping</h6>
              <h6 class="text-light-grey">$3.99 USD</h6>
            </div>

            <div class="checkout-pricing-text">
              <h6 class="text-light-grey">Discount 15%</h6>
              <h6 class="text-light-grey">-$4.20 USD</h6>
            </div>
            <div class="checkout-pricing-text">
              <h6>Sub Total</h6>
              <h6>$27.78 USD</h6>
            </div>
          </div>
        </div>
        <hr />

        <div class="order-main-total-view">
          <h5>Order Total</h5>
          <h5>$27.78 USD</h5>
        </div>

        <whycontent></whycontent>
      </div>
    </div>
  </div>
</template>

<script>
import WhyContentComponent from "../components/why-content";
import image from "../assets/images/cards.png";
import paypal from "../assets/images/paypal.png";
import tshirt from "../assets/images/t-shirt.png";

export default {
  name: "checkout-component",
  components: {
    whycontent: WhyContentComponent,
  },

  data: function () {
    return {
      image: image,
      paypal: paypal,
      tshirt: tshirt,
    };
  },
};
</script>

<style>
</style>