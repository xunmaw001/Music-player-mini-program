<template>
    <view class="content">
        <form class="app-update-pv">
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">音乐名称</view>
                <input   disabled
                         :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.yinyueName" type="text" v-model="ruleForm.yinyueName" placeholder="音乐名称"></input>
            </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">音乐编号</view>
                <input   disabled
                         :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.yinyueUuidNumber" type="text" v-model="ruleForm.yinyueUuidNumber" placeholder="音乐编号"></input>
            </view>
                <view
                        :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(218, 220, 219, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"108rpx"}'
                        class="cu-form-group" @tap="yinyuePhotoTap">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">图片</view>
                    <view class="right-input" style="padding:0;textAlign:left">
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-if="ruleForm.yinyuePhoto" :src="baseUrl+ruleForm.yinyuePhoto" mode="aspectFill">
                        </image>
                        <image  :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
                    </view>
                </view>
					            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">关键字</view>
                <input   disabled
                         :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                         :disabled="ro.yinyueGuanjianzi" type="text" v-model="ruleForm.yinyueGuanjianzi" placeholder="关键字"></input>
            </view>
                <view
                        :style='{"boxShadow":"0 0 0px rgba(0,0,0,.3)","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(218, 220, 219, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"108rpx"}'
                        class="cu-form-group" @tap="yinyueMusicTap">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">音乐</view>
                    <view class="right-input" style="padding:0;textAlign:left">
                        <image
                                :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-if="ruleForm.yinyueMusic" :src="baseUrl+ruleForm.yinyueMusic" mode="aspectFill">
                        </image>
                        <image  :style='{"width":"68rpx","boxShadow":"0 0 0px rgba(0,0,0,.3)","borderRadius":"100%","textAlign":"left","height":"68rpx"}'
                                class="avator" v-else src="../../static/gen/upload.png" mode="aspectFill"></image>
                    </view>
                </view>
					                <view :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                      class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">音乐类型</view>
                    <picker @change="yinyueTypesChange" :value="yinyueTypesIndex" :range="yinyueTypesOptions" range-key="indexName">
                        <view
                                :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                                class="uni-input">{{ruleForm.yinyueTypes?ruleForm.yinyueValue:"请选择音乐类型"}}</view>
                    </picker>
                </view>
                <view :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"100rpx"}'
                      class="cu-form-group">
                    <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                          class="title">二级类型</view>
                    <picker @change="yinyueErjiTypesChange" :value="yinyueErjiTypesIndex" :range="yinyueErjiTypesOptions" range-key="indexName">
                        <view
                                :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx"}'
                                class="uni-input">{{ruleForm.yinyueErjiTypes?ruleForm.yinyueErjiValue:"请选择二级类型"}}</view>
                    </picker>
                </view>
            <view
                    :style='{"boxShadow":"0","backgroundColor":"rgba(255, 255, 255, 0.25)","borderColor":"rgba(228, 232, 230, 1)","margin":"0 0 0px 0","borderWidth":"2rpx","borderStyle":"none none solid none ","height":"210rpx"}'
                    class="cu-form-group">
                <view :style='{"width":"160rpx","fontSize":"28rpx","color":"var(--publicMainColor)","textAlign":"left"}'
                      class="title">音乐介绍</view>
                <textarea :style='{"padding":"0 30rpx","boxShadow":"0 0 0px rgba(0,0,0,.6) inset","margin":"0","borderColor":"var(--publicMainColor)","backgroundColor":"#fff","color":"rgba(0, 0, 0, 1)","textAlign":"left","borderRadius":"0","borderWidth":"10rpx 2rpx","fontSize":"28rpx","borderStyle":"solid","height":"88rpx","marginTop":"7rpx","height":"200rpx"}'
                          :disabled="ro.yinyueContent" v-model="ruleForm.yinyueContent" placeholder="音乐介绍"/>
            </view>

            <view class="btn">
                <button
                        :style='{"boxShadow":"0 0 16rpx rgba(0,0,0,0) inset","backgroundColor":"var(--publicMainColor)","borderColor":"#409EFF","borderRadius":"8rpx","color":"rgba(255, 255, 255, 1)","borderWidth":"0","width":"70%","fontSize":"32rpx","borderStyle":"solid","height":"80rpx"}'
                        @tap="onSubmitTap" class="bg-red">提交</button>
            </view>
        </form>

					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="insertTimeConfirm"
                              ref="insertTime" themeColor="#333333"></w-picker>
					<w-picker mode="dateTime" step="1" :current="false" :hasSecond="false" @confirm="createTimeConfirm"
                              ref="createTime" themeColor="#333333"></w-picker>


    </view>
</template>

<script>
    import wPicker from "@/components/w-picker/w-picker.vue";

    export default {
        data() {
            return {
                cross: '',
                ro:{
					yinyueName: false,
					yinyueUuidNumber: true,
					yinyuePhoto: false,
					zanNumber: false,
					caiNumber: false,
					yinyueGuanjianzi: false,
					yinyueMusic: false,
					yinyueTypes: false,
					yinyueErjiTypes: false,
					yinyueContent: false,
					shangxiaTypes: false,
					yinyueDelete: false,
					insertTime: false,
					createTime: false,
        },
            ruleForm: {
					yinyueName: '',
					yinyueUuidNumber: this.getUUID(),//数字
					yinyuePhoto: '',
					zanNumber: '',
					caiNumber: '',
					yinyueGuanjianzi: '',
					yinyueMusic: '',
					yinyueTypes: '',//数字
					yinyueValue: '',//数字对应的值
					yinyueErjiTypes: '',//数字
					yinyueErjiValue: '',//数字对应的值
					yinyueContent: '',
					shangxiaTypes: '',//数字
					shangxiaValue: '',//数字对应的值
					yinyueDelete: '',
					insertTime: '',
					createTime: '',
            },
            // 登陆用户信息
            user: {},
            yinyueTypesOptions: [],
            yinyueTypesIndex : 0,
            yinyueErjiTypesOptions: [],
            yinyueErjiTypesIndex : 0,
            shangxiaTypesOptions: [],
            shangxiaTypesIndex : 0,

        }
        },
        components: {
            wPicker
        },
        computed: {
            baseUrl() {
                return this.$base.url;
            },
        },
        async onLoad(options) {
		/*下拉框*/
			let yinyueTypesParams = {
                page: 1,
                limit: 100,
                dicCode: 'yinyue_types',
            }
			let yinyueTypes = await this.$api.page(`dictionary`, yinyueTypesParams);
			this.yinyueTypesOptions = yinyueTypes.data.list
		/*下拉框*/
			let yinyueErjiTypesParams = {
                page: 1,
                limit: 100,
                dicCode: 'yinyue_erji_types',
            }
			let yinyueErjiTypes = await this.$api.page(`dictionary`, yinyueErjiTypesParams);
			this.yinyueErjiTypesOptions = yinyueErjiTypes.data.list
		/*下拉框*/
			let shangxiaTypesParams = {
                page: 1,
                limit: 100,
                dicCode: 'shangxia_types',
            }
			let shangxiaTypes = await this.$api.page(`dictionary`, shangxiaTypesParams);
			this.shangxiaTypesOptions = shangxiaTypes.data.list


            // 如果是更新操作
            if (options.id) {
                this.ruleForm.id = options.id;
                // 获取信息
                let res = await this.$api.info(`yinyue`, this.ruleForm.id);
                this.ruleForm = res.data;
            }
            if(options.yinyueId){
                this.ruleForm.yinyueId = options.yinyueId;
            }
            // 跨表
            // this.styleChange()
        },
        methods: {
            // 下拉变化
            yinyueTypesChange(e) {
                this.yinyueTypesIndex = e.target.value
                this.ruleForm.yinyueValue = this.yinyueTypesOptions[this.yinyueTypesIndex].indexName
                this.ruleForm.yinyueTypes = this.yinyueTypesOptions[this.yinyueTypesIndex].codeIndex
            },
            yinyueErjiTypesChange(e) {
                this.yinyueErjiTypesIndex = e.target.value
                this.ruleForm.yinyueErjiValue = this.yinyueErjiTypesOptions[this.yinyueErjiTypesIndex].indexName
                this.ruleForm.yinyueErjiTypes = this.yinyueErjiTypesOptions[this.yinyueErjiTypesIndex].codeIndex
            },
            shangxiaTypesChange(e) {
                this.shangxiaTypesIndex = e.target.value
                this.ruleForm.shangxiaValue = this.shangxiaTypesOptions[this.shangxiaTypesIndex].indexName
                this.ruleForm.shangxiaTypes = this.shangxiaTypesOptions[this.shangxiaTypesIndex].codeIndex
            },
            // styleChange() {
            // 	this.$nextTick(() => {
            // 		// document.querySelectorAll('.app-update-pv .cu-form-group .uni-yaoxianStyle-yaoxianStyle').forEach(el=>{
            // 		//   el.style.backgroundColor = this.addUpdateForm.yaoxianStyle.content.backgroundColor
            // 		// })
            // 	})
            // },
			yinyuePhotoTap() {
                let _this = this;
                this.$api.upload(function(res) {
                    _this.ruleForm.yinyuePhoto = 'upload/' + res.file;
                    _this.$forceUpdate();
                    _this.$nextTick(() => {
                        // _this.styleChange()
                    })
                });
            },
			yinyueMusicTap() {
                let _this = this;
                this.$api.upload(function(res) {
                    _this.ruleForm.yinyueMusic = 'upload/' + res.file;
                    _this.$forceUpdate();
                    _this.$nextTick(() => {
                        // _this.styleChange()
                    })
                });
            },
			// 日期控件
			insertTimeConfirm(val) {
                this.ruleForm.insertTime = val.result;
                this.$forceUpdate();
            },
			// 日期控件
			createTimeConfirm(val) {
                this.ruleForm.createTime = val.result;
                this.$forceUpdate();
            },

            getUUID() {
                return new Date().getTime();
            },
            async onSubmitTap() {
				if ((!this.ruleForm.yinyueName)) {
                    this.$utils.msg(`音乐名称不能为空`);
                    return
                }
				if ((!this.ruleForm.yinyueUuidNumber)) {
                    this.$utils.msg(`音乐编号不能为空`);
                    return
                }
				if ((!this.ruleForm.yinyuePhoto)) {
                    this.$utils.msg(`图片不能为空`);
                    return
                }
				if ((!this.ruleForm.zanNumber) && (!this.$validate.isIntNumer(this.ruleForm.zanNumber)) && this.ruleForm.zanNumber >0) {
                    this.$utils.msg(`赞不能为空，不能小于0 格式为数字`);
                    return
                }
				if ((!this.ruleForm.caiNumber) && (!this.$validate.isIntNumer(this.ruleForm.caiNumber)) && this.ruleForm.caiNumber >0) {
                    this.$utils.msg(`踩不能为空，不能小于0 格式为数字`);
                    return
                }
				if ((!this.ruleForm.yinyueGuanjianzi)) {
                    this.$utils.msg(`关键字不能为空`);
                    return
                }
				if ((!this.ruleForm.yinyueErjiTypes)) {
                    this.$utils.msg(`二级类型不能为空`);
                    return
                }
                if (this.ruleForm.id) {
                    await this.$api.update(`yinyue`, this.ruleForm);
                } else {
                    await this.$api.save(`yinyue`, this.ruleForm);
                }
                uni.setStorageSync('pingluenStateState', true);
                this.$utils.msgBack('提交成功');
            },
            getDate(type) {
                const date = new Date();
                let year = date.getFullYear();
                let month = date.getMonth() + 1;
                let day = date.getDate();
                if (type === 'start') {
                    year = year - 60;
                } else if (type === 'end') {
                    year = year + 2;
                }
                month = month > 9 ? month : '0' + month;;
                day = day > 9 ? day : '0' + day;
                return `${year}-${month}-${day}`;
            },
            toggleTab(str) {
                this.$refs[str].show();
            }
        }
    }
</script>
<style lang="scss" scoped>
    .container {
        padding: 20upx;
    }

    .content:after {
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        bottom: 0;
        content: '';
        background-attachment: fixed;
        background-size: cover;
        background-position: center;
    }

    textarea {
        border: 1upx solid #EEEEEE;
        border-radius: 20upx;
        padding: 20upx;
    }

    .title {
        width: 180upx;
    }

    .avator {
        width: 150upx;
        height: 60upx;
    }

    .right-input {
        flex: 1;
        text-align: left;
        padding: 0 24upx;
    }

    .cu-form-group.active {
        justify-content: space-between;
    }

    .cu-form-group .title {
        height: auto;
        line-height:30rpx
    }

    .btn {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20upx 0;
    }

    .cu-form-group {
        padding: 0 24upx;
        background-color: transparent;
        min-height: inherit;
    }

    .cu-form-group+.cu-form-group {
        border: 0;
    }

    .cu-form-group uni-input {
        padding: 0 30upx;
    }

    .uni-input {
        padding: 0 30upx;
    }

    .cu-form-group uni-textarea {
        padding: 30upx;
        margin: 0;
    }

    .cu-form-group uni-picker::after {
        line-height: 80rpx;
    }

    .select .uni-input {
        line-height: 80rpx;
    }

    .input .right-input {
        line-height: 88rpx;
    }
</style>