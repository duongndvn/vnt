<template>
  <form @submit="onSubmit">
    <h3>Thêm chuyến đi mới</h3>
    <!-- <div v-if="phoneIsRegited" class="alert alert-danger" role="alert">
      Số điện thoại này đã được đăng ký.
    </div> -->
    <div class="form-group field">
      <label for="name">Tên công ty vận tải</label>
      <input
        type="text"
        class="form-control"
        id="name"
        placeholder="Tên công ty vận tải"
        v-model="name"
        required
      />
    </div>
    <div class="form-group field">
      <label for="phone">Số điện thoại</label>
      <input
        type="text"
        class="form-control"
        id="phone"
        placeholder="0123456789"
        v-model="phone"
        required
      />
    </div>
    <div class="form-group field">
      <label for="description">Mô tả</label>
      <textarea
        class="form-control"
        id="description"
        rows="3"
        v-model="description"
      ></textarea>
    </div>
    <div class="form-group field">
      <div class="group-button">
        <button type="submit" class="btn btn-primary mr-30">Thêm</button>
        <button
          type="submit"
          class="btn btn-outline-danger"
          @click="TOGGLE_ISADDNEW"
        >
          Ẩn bớt
        </button>
      </div>
    </div>
  </form>
</template>

<script>
import { mapActions, mapGetters, mapMutations } from "vuex";
export default {
  data() {
    return {
      type: "",
      phone: "",
      license_plate: "",
    };
  },
  
  computed: mapGetters(["id", "failed", "vehicles", "vehicle_type", "id_transportation"]),
  methods: {
    
    ...mapMutations(["SET_ALL_VEHICLE_TYPE"]),
    ...mapActions(["addVehicle"]),
    onSubmit(event) {
      event.preventDefault();
      this.addVehicle({
        type: this.type,
        phone: this.phone,
        license_plate: this.license_plate,
        id_transportation: this.id_transportation
      });
      this.type = "";
      this.phone = "";
      this.license_plate = "";
    },
  },
};
</script>

<style scoped>
h3 {
  margin-bottom: 20px;
}
.field {
  display: flex;
  margin-top: 10px;
}
.field label {
  width: 30%;
  vertical-align: middle;
  margin: 0px;
  font-weight: bold;
}
.group-button {
  margin: auto;
}
.field button {
  width: 85px;
  height: 40px;
}
.mr-30 {
  margin-right: 30px;
}
</style>