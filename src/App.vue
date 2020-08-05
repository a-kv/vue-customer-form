<template>
    <div id="app" class="main">
        <form class="form" @submit.prevent="onSubmit" v-if=isVisibleForm>
            <span class="title">CREATE CUSTOMER</span>
            <div class="customer-form">
                <div class="field">
                    <label for="lastName">Last name* </label>
                    <div class="input-field">
                        <input
                                id="lastName"
                                type="text"
                                v-model.trim="lastName"
                                :class="$v.lastName.$dirty && !$v.lastName.required">
                        <small
                                class="helper-text invalid"
                                v-if="$v.lastName.$dirty && !$v.lastName.required"
                        >Field is required</small>
                    </div>
                </div>
                <div class="field">
                    <label for="firstName">First name* </label>
                    <div class="input-field">
                        <input
                                id="firstName"
                                type="text"
                                v-model.trim="firstName"
                                :class="$v.firstName.$dirty && !$v.firstName.required">
                        <small
                                class="helper-text invalid"
                                v-if="$v.firstName.$dirty && !$v.firstName.required"
                        >Field is required</small>
                    </div>
                </div>
                <div class="field">
                    <label for="middleName">Middle name</label>
                    <div class="input-field">
                        <input
                                id="middleName"
                                type="text"
                                v-model.trim="middleName"
                        />
                    </div>
                </div>
                <div class="info-block">
                    <div class="field">
                        <label for="numberPhone">Phone* </label>
                        <div class="input-field">
                            <input
                                    id="numberPhone"
                                    type="text"
                                    maxlength="12"
                                    placeholder="+7(911)111 11 11"
                                    pattern="\+7\s?[\(]{0,1}9[0-9]{2}[\)]{0,1}\s?\d{3}[-]{0,1}\d{2}[-]{0,1}\d{2}"

                                    v-model.trim="numberPhone"
                                    :class="$v.numberPhone.$dirty && !$v.numberPhone.required">
                            <small
                                    class="helper-text invalid"
                                    v-if="$v.numberPhone.$dirty && !$v.numberPhone.required"
                            >Field is required</small>
                        </div>
                    </div>
                    <div class="field">
                        <label for="birth">Birth* </label>
                        <div class="input-field">
                            <input id="birth"
                                   type="date"
                                   v-model="birth"
                                   :class="$v.birth.$dirty && !$v.birth.required">
                            <small
                                    class="helper-text invalid"
                                    v-if="$v.birth.$dirty && !$v.birth.required"
                            >Field is required</small>
                        </div>
                    </div>
                    <div class="field">
                        <label for="gender">Gender</label>
                        <div class="select-field">
                            <select id="gender">
                                <option selected disabled>
                                    Choose client gender
                                </option>
                                <option>
                                    Male
                                </option>
                                <option>
                                    Female
                                </option>
                            </select>

                        </div>
                    </div>
                    <div class="field">
                        <label for="clientGroup">Group*</label>
                        <div class="select-field">
                            <select id="clientGroup">
                                <option selected disabled>
                                    Choose client group
                                </option>
                                <option value="VIP">
                                    VIP
                                </option>
                                <option value="OMS">
                                    OMS
                                </option>
                                <option value="Problematic">
                                    Problematic
                                </option>
                                <small class="helper-text invalid"
                                       v-if="$v.clientGroup.$dirty && !$v.clientGroup.required"
                                >Field is required</small>
                            </select>
                        </div>
                    </div>
                    <div class="field">
                        <label for="attendDoc">Attending doctor* </label>
                        <div class="select-field">
                            <select :selected="attendDoc" v-model="attendDoc" id="attendDoc">
                                <option selected disabled>
                                    Choose attending doctor
                                </option>
                                <option value="Ivanov">
                                    Ivanov
                                </option>
                                <option value="Zakharov">
                                    Zakharov
                                </option>
                                <option value="Chernysheva">
                                    Chernysheva
                                </option>
                            </select>
                            <small class="helper-text invalid"
                                   v-if="$v.attendDoc.$dirty && !$v.attendDoc.required"
                            >Field is required</small>
                        </div>
                    </div>
                    <div class="field">
                        <label for="sendSms">SMS</label>
                        <div class="select-field">
                            <input v-model="sendSms"
                                   id="sendSms" type="checkbox"/>
                        </div>
                    </div>
                </div>
                <span class="title">Address</span>
                <div class="info-block">
                    <div class="field">
                        <label for="zipCode">Zip code</label>
                        <div class="input-field">
                            <input
                                    id="zipCode"
                                    type="text"
                                    v-model.trim="zipCode">
                        </div>
                    </div>
                    <div class="field">
                        <label for="country">Country</label>
                        <div class="input-field">
                            <input
                                    id="country"
                                    type="text"
                                    v-model.trim="country">
                        </div>
                    </div>
                    <div class="field">
                        <label for="region">Region</label>
                        <div class="input-field">
                            <input
                                    id="region"
                                    type="text"
                                    v-model.trim="region">
                        </div>
                    </div>
                    <div class="field">
                        <label for="city">City*</label>
                        <div class="input-field">
                            <input
                                    id="city"
                                    type="text"
                                    v-model.trim="city"
                                    :class="$v.city.$dirty && !$v.city.required">
                            <small
                                    class="helper-text invalid"
                                    v-if="$v.city.$dirty && !$v.city.required"
                            >Field is required</small>
                        </div>
                    </div>
                    <div class="field">
                        <label for="street">Street</label>
                        <div class="input-field">
                            <input
                                    id="street"
                                    type="text"
                                    v-model.trim="street"
                            />
                        </div>
                    </div>
                    <div class="field">
                        <label for="house">House</label>
                        <div class="input-field">
                            <input
                                    id="house"
                                    type="text"
                                    v-model.trim="house">
                        </div>
                    </div>
                </div>
                <span class="title">Document</span>
                <div class="info-block">
                    <div class="field">
                        <label for="documentType">Document*</label>
                        <div class="select-field">
                            <select :selected="documentType" v-model="documentType" id="documentType">
                                <option selected disabled>
                                    Choose document type
                                </option>
                                <option value="Passport">
                                    Passport
                                </option>
                                <option value="Birth certificate">
                                    Birth certificate
                                </option>
                                <option value="Driver's license">
                                    Driver's license
                                </option>
                            </select>
                            <small
                                    class="helper-text invalid"
                                    v-if="$v.documentType.$dirty && !$v.documentType.required"
                            >Field is required</small>
                        </div>
                    </div>
                    <div class="field">
                        <label for="seriesPassport">Series</label>
                        <div class="input-field">
                            <input type="text"
                                   id="seriesPassport"/>
                        </div>
                    </div>
                    <div class="field">
                        <label for="numberPassport">Number</label>
                        <div class="input-field">
                            <input
                                    id="numberPassport"
                                    type="text"
                                    v-model.trim="numberPassport">
                        </div>
                    </div>
                    <div class="field">
                        <label for="dateOfIssue">Date of issue* </label>
                        <div class="input-field">
                            <input type="date"
                                   id="dateOfIssue"
                                   v-model="dateOfIssue"
                                   :class="$v.dateOfIssue.$dirty && !$v.dateOfIssue.required"/>

                            <small
                                    class="helper-text invalid"
                                    v-if="$v.dateOfIssue.$dirty && !$v.dateOfIssue.required"
                            >Field is required</small>
                        </div>
                    </div>
                </div>
                <div class="field">
                    <label for="issuedBy">Issued by</label>
                    <div class="input-field">
                        <input
                                id="issuedBy"
                                type="text"
                                v-model.trim="issuedBy">
                    </div>
                </div>
                <button v-on:click="isVisible"
                        class="btn-submit"
                        type="submit">

                    CREATE
                </button>
            </div>
        </form>
        <div class="massage" id="form" v-if=isVisibleMess>
            Successful client creation
            <button v-on:click="reload()">
                CREATE NEW CUSTOMER
            </button>
        </div>
    </div>
</template>

<script>

    import {required} from 'vuelidate/lib/validators'

    export default {
        name: 'App',

        data: () => ({
            lastName: '',
            firstName: '',
            middleName: '',
            birth: '',
            numberPhone: '',
            gender: '',
            attendDoc: '',
            clientGroup: [],
            sendSms: false,
            zipCode: '',
            country: '',
            region: '',
            city: '',
            street: ' ',
            house: '',
            documentType: '',
            seriesPassport: '',
            numberPassport: '',
            issuedBy: '',
            dateOfIssue: '',
            isVisibleForm: true,
            isVisibleMess: false,
            isSuccess: false
        }),
        validations: {
            lastName: {required},
            firstName: {required},
            numberPhone: {required},
            birth: {required},
            clientGroup: {required},
            attendDoc: {required},
            city: {required},
            documentType: {required},
            dateOfIssue: {required},

        },
        methods: {
            onSubmit() {
                if (this.$v.$invalid) {
                    this.$v.$touch()
                    this.isSuccess = true;
                    const formData = {
                        lastName: this.lastName,
                        firstName: this.firstName,
                        birth: this.birth,
                        numberPhone: this.numberPhone,
                        middleName: this.middleName,
                        gender: this.gender,
                        clientGroup: this.clientGroup,
                        attendDoc: this.attendDoc,
                        sendSms: this.sendSms,
                        zipCode: this.zipCode,
                        country: this.country,
                        region: this.region,
                        city: this.city,
                        street: this.street,
                        house: this.house,
                        documentType: this.documentType,
                        seriesPassport: this.seriesPassport,
                        numberPassport: this.numberPassport,
                        issuedBy: this.issuedBy,
                        dateOfIssue: this.dateOfIssue,
                    }
                    localStorage.setItem('customer', JSON.stringify({formData}));
                } else {
                    console.log('error')
                    return false
                }
            },
            isVisible() {
                if (this.isSuccess === true) {
                    this.isVisibleMess = !this.isVisibleMess,
                        this.isVisibleForm = !this.isVisibleForm
                        this.lastName = '',
                        this.firstName = '',
                        this.middleName = '',
                        this.birth = '',
                        this.numberPhone = '',
                        this.gender = '',
                        this.attendDoc = '',
                        this.clientGroup = [],
                        this.sendSms = false,
                        this.zipCode = '',
                        this.country = '',
                        this.region = '',
                        this.city = '',
                        this.street = ' ',
                        this.house = '',
                        this.documentType = '',
                        this.seriesPassport = '',
                        this.numberPassport = '',
                        this.issuedBy = '',
                        this.dateOfIssue = ''
                }

            },
            reload(){
                location.reload()
            }

        }
    }
</script>

<style lang="scss" scoped>
    .main {
        .form {
            display: flex;
            flex-direction: column;
            width: 45%;
            min-height: 93vh;
            min-width: 320px;
            border-radius: 5px;
            margin: 2% auto;
            box-shadow: 0 9px 50px hsla(0, 2%, 8%, 0.31);
            padding: 2%;
            background-color: #ffffff;;

            .title {
                display: flex;
                margin: 2% auto 5% auto;
                text-align: center;
            }

            .customer-form {
                display: flex;
                flex-direction: column;

                .field {
                    display: flex;
                    flex-direction: row;
                    width: 100%;
                    justify-content: space-between;
                    height: 45px;

                    & label {
                        display: flex;
                        width: 120px;

                    }

                    .input-field {
                        display: flex;
                        flex-direction: column;
                        width: 100%;

                        & input {
                            display: flex;
                            min-width: 200px;
                            border: none;
                            border-bottom: 1px solid #9e9e9e;
                            background: #fff;
                            color: #333;
                            position: relative;
                        }

                        & input:active, & input:focus {
                            outline: none;
                            background-color: #f3f3f3;
                            transition: 0.2s;
                            border-radius: 2px;

                        }

                        & small {
                            position: absolute;
                            margin-top: 20px;
                            color: #ec0202;
                        }
                    }
                }

                .info-block {
                    display: flex;
                    flex-wrap: wrap;
                    width: 100%;
                    justify-content: space-between;

                    .field {
                        display: flex;
                        width: 320px;

                        .input-field {
                            & input {
                                display: flex;
                                min-width: 100px;
                            }
                        }

                        .select-field {
                            display: flex;
                            width: 100%;
                            flex-direction: column;

                            & select {
                                width: 100%;
                                border: none;
                                border-bottom: 1px solid #9e9e9e;
                                outline: none;

                                & option, & option:active {
                                    background-color: #b3b3b3;
                                    outline: none;
                                    border: none;
                                }
                            }

                            & small {
                                position: absolute;
                                margin-top: 20px;
                                color: #ec0202;
                            }
                        }
                    }
                }
            }

            & button {
                display: inline-block;
                color: #252537;

                width: 280px;
                height: 50px;

                padding: 0 20px;
                background: #b3b3b3;
                border-radius: 3px;

                outline: none;
                border: none;

                cursor: pointer;
                text-align: center;
                transition: all 0.2s linear;

                margin: 7% auto;
                letter-spacing: 0.05em;
            }

            & button:hover {
                box-shadow: 3px 3px rgba(16, 40, 101, 0.91);
            }

        }

        .massage {
            display: flex;
            align-items: center;
            flex-direction: column;
            justify-content: center;
            width: 350px;
            height: 350px;
            border-radius: 5px;
            margin: 2% auto;
            box-shadow: 0 9px 50px hsla(0, 2%, 8%, 0.31);
            padding: 2%;
            background-color: #ffffff;

            button {
                display: inline-block;
                color: #252537;

                width: 280px;
                height: 50px;

                padding: 0 20px;
                background: #b3b3b3;
                border-radius: 3px;

                outline: none;
                border: none;

                cursor: pointer;
                text-align: center;
                transition: all 0.2s linear;

                margin: 7% auto;
                letter-spacing: 0.05em;
            }

            button:hover {
                box-shadow: 3px 3px rgba(16, 40, 101, 0.91);
            }
        }

    }
</style>
