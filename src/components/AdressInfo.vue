<template>
  <div class=adress-info-container>
    <div class=adress-form>
      <select v-model="coin_type">
        <option value="bitcoin">Bitcoin</option>
        <option value="litecoin">Litecoin</option>
        <option value="bitcoin-cash">Bitcoin Cash</option>
      </select>
      <input v-model="adress" placeholder="Adress">
      <button @click="get_adress_info" class=search_adress_button>Search</button>
    </div>

    <div class=adress-display-container>

    </div>

    <div class=record-container>
      <button v-if="valid_adress" @click="get_transactions_info">Show last 10 transactions</button>
      <TransactionRecord v-bind:transactions="transactions_details"/>
    </div>
  </div>
</template>

<script>
import TransactionRecord from './TransactionRecord.vue'

export default {
  name: 'AdressInfo',
  props: {
    msg: String
  },
  data () {
    return {
      // Shows the history or not
      valid_adress: false,
      // Adress input
      adress: "",
      // Selected coin
      coin_type: "bitcoin",
      // Full answer given by the API
      resquest_data: null,
      // Adress info given by the API
      adress_info: [],
      // Transactions related to the adress
      transactions: [],
      // Ultimas 10 transacciones
      last_transactions: [],
      // Utxos given by the API
      utxo: [],
      // Transactions details obtained using the second API call
      transactions_details: {}
    }
  },
  methods: {
    get_adress_info: function() {
      // Clear transactionr record
      this.transactions_details = {}
      
      // Fake api call
      let response = { 
        "data": {
          "data": {
            "1J1F3U7gHrCjsEsRimDJ3oYBiV24wA8FuV": {
              "address": {
                "type":"pubkeyhash",
                "script_hex":"76a914ba85dc466140d3ef2eac3f7e42088ec501315a4b88ac",
                "balance":800000030000,
                "balance_usd":89515203.35681999,
                "received":39660344246683,
                "received_usd":2231092778.8083,
                "spent":38860344216683,
                "spent_usd":2164916650.3045,
                "output_count":2336,
                "unspent_output_count":2,
                "first_seen_receiving":"2011-05-28 02:38:12",
                "last_seen_receiving":"2020-07-27 17:58:48",
                "first_seen_spending":"2011-05-28 02:54:48",
                "last_seen_spending":"2020-07-27 16:40:36",
                "scripthash_type":null,
                "transaction_count":2859
              },
              "transactions": [
                "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                "1a82b98fd2eeb8917b4c83ed8690219efea6e0353681768099f049763a99e87f",
                "45dfaaa77a6f45bdf9a0e9b50f784badfc0ae19a1a17a1eaadf59b3f8b9bc119",
                "09a879bffc86e039d6757692de2fafa9587e626c89f580bf0f6802eb5c7dc39d",
                "0f9a647e741339cb6747663c469bd30764f1938b8a820e6076e419acd186f9ed",
                "1011db78cec5a09cfb68e2de004d3c0f989da1c438c5e3db3e53b605746d1def",
                "3bc4a25c2d514e5510eaf3ac09ae2e7e893e27662ebac5e4838d3427ecf25440",
                "38b6c546ba61bbfe95d919da39770bf3ce0a491c4e507d6c7b76aa8da69d1fd3",
                "8faea4db65fe4436ea9eab8f059deecf5c6e8217661f280d130bc50446f742b8",
                "3712c026c78bb17f9d3de808b9f8bc8c5b3e4b00477261796314fecdb7144a91",
                "0ba49689558ef24fbf0702621ad92f8275302f8b83b1f51e394560d66b096d73",
                "fd27d7b865f95059a1762d3f70b9e1798fd5660f77f060f23a5982e733489884",
                "c55e8cabf4f5240ab4ecdb9ca120628a9eda19795d1e2b81c11d69ac2f0f5f68",
                "f02c7ec0e11b087565a43a7567c25c4dfd0d805f80e964ab35ca700e5fcaf6ec",
                "b1237e99e297d0f4835471e9ecdf8f67350696d65c420c988c5c1bec72e519a1",
                "0c7a44057283fa7da8372971d300997fb59f850fe0edc5d1d9fcebeeeadbd0cb",
                "9074b7861647112274e5a368d119dd588c113d37a654f8814b52de4a9fe04cfd",
                "58789af045bcba59220eed73c2de361b863b17417e23413f716cfefd6cf34849",
                "549ea4ca64a2544266c19eb7294d76c055e080a832939466eec5b2707eaa1bd1",
                "50d9ce38f04753a70c6b9d794b1125509ed2269d4932a4c2572e9658cfd9db3b",
                "b2df79c1a8ee10be0ff06e1e40412e77687b2e474e3f5e3a81ea7970500bf915",
                "5f0a515bdf6f1276bffd216c6451821318cc4629a05d15aae04a8de9b01f99e3",
                "7e1b0da232f021108f4ba88b225a14417b1d51addabb677e9da7bdf5ddf1b8c6",
                "167b8bbf994e299afa68332398a4bb4d9095d48ce4b565a6d90c0b2b7d5e7766",
                "809273eb13cdc73404a10b4d020617a1bb36057c0d467831180352d2e9f95491",
                "e664e204cb1185800541bcf1ee37d750b107f97232f15a789e2427a8023309db",
                "c472291e6811607e6b5cfb1694d684ca7363a2b5e6418893270df7a47e75823a",
                "72b11bbb177da07ee57304120d9e3bb995ef8f2a7f3e551c5902f17a1f3caf5d",
                "4602aa4577c65f7a53c9fd6acbea195ff661055d1f65a859ae82f7ae7c6245b5",
                "427112d9b023ba3147481b7787611afe02ffb4d3a2c090fad96f340e05e0fce1",
                "3a3aa69ac345132479117f54c119670cb4baaef56defcab4baf5b25324b6d012",
                "a146107a51c2a1bce41e8d2c681c2d0cb6595d7f9f17bed6e10e620057980842",
                "4d1fdb6b60e9ee1a491ce38bab034440790fd6b768d2d366989680146a1b1e8d",
                "d44f0b9cbe20ec3464e62b3c945a7015e7c5d7c097015e0f8b91e5c177dec643",
                "b1a96f9e5732087500061c9ceef113c99b133bbe2027b91d75764fe56865c994",
                "74b3b655320d7305712f3d7f0233039841418985f5baad7472c14132fcd0a87b",
                "e7f14c682978b349fcab63fb673fbdd0253284b0d26f9e3bebac2b1777b0eb55",
                "66a237c86cbd48bd62b4fe703f795c392a60f6871ad6743dbc35f4174d7f422b",
                "f87c9a339696d4c322de71fa0b6946d5356ba1d2a901429c832ee7c5b1a25c9f",
                "730b4239f0cad9ce3c78e9296c66b4596cafde309002c748f88fa3b6e3f8684a",
                "2b52b7b02f4da3369d4427cab7a7f0a60184afcb20d4bba54afa09e299060406",
                "32b0dd5c85dc2783f476abfb130020584e3d6dee620ec3c932215df8009195ad",
                "5ca18a09e0219432d644f7cec3451f11d1592ef0ab63c0b72e575a3ac50b79d3",
                "9328be82fd0ee5aa6942089c2e9d39e64ab43569413b0b38f8deed59e5c47a0b",
                "7a4da9db9d2a491f8fdc4674e1228bae3f20bffb1617240775af8dd4ef76506b",
                "53f2d1c7e52df0cb40e892e7b295cc97497bc834f7688cba9e386a546e6042d0",
                "2e9de8b0445aed2ce72fadf12c997a63824f3991d657c3d2bdd84651ec1aba0e",
                "2fe8c9c60a700fa2d12b566fc19f9df23d18b7fc171871cf5715a1a470d9ba58",
                "dcc5ed840cc4f3760fd3e674ae253a1b722ba7b7cb5c4a9d10d8d1dc645bb12d",
                "8bf1f7985ebdd5b88833619b60f4d30d34d47a4ea5515830956360ccef677956",
                "bc922c0c09835156b49d8916d67ef3ec3a080653e5bc6655c7795ca62e862a73",
                "02f6988658378088147c070816a53efe900e2eca1eb584e878d500a6c2253bc7",
                "49d166cce9dff237eaf2421ea9b1f194e1724e570c1998347bd945d2a5a85b70",
                "6f9af7e49aa09e86464ecf03228e54935580522901a7e80b9904ce8a903f31a9",
                "7d971593a5a050118322fca99ea4533e07633bb569e2094952ae20373d2f0f44",
                "f5b47bbb64e2690676b6e07d2c8c722f0cb0e9d4b8baa0cd4a9d3e208fc9bda4",
                "113979a384d7a766a0e5e675f10af19f682e24f2de8163b1f08bd021b8478773",
                "9c04ceaad764989cc05f9f5c23b48770ee74c400941da4f23e62f5a3cd8fca9e",
                "3ee76271f229ffb89aeffd121360076132e16295aa6d2b17290103528deae0bf",
                "1279793b9d79eb20a0887baebb91d5c282698e76466565411ee2eabd9be44610",
                "3baa38bb98adbf602424834f524c8b45c86328b64a4e1a0115e2464ced0d94c6",
                "fbed5bcde1104663b50036bfaf75139be74371e511d04d9b9ad83ce906d79dcd",
                "b4c24e55d1a505150e2778620576f42b0d5be8621ba14e2f93c2b4ae076b0c7d",
                "56ccda74be878fa33db013d9d6b1d24166ff469df58ef8b763a571a1292f936a",
                "256b0f8d49be6eacfb270a6dc973db7d3143768bfda93d4410e0153f5782da54",
                "ececf93777427d0e5b22b876692ca8729e4639182d17fc2f0c80d7144c4fe6ff",
                "a7c1ef34964794b0a0aef82d663cfa1579c53411c59271299e102a12ea345916",
                "7967089529c8fa8035910cebcb1c5c474f94defe8b18fb2b67b0fad6a378892a",
                "08af58957473f7644cf2d677a3326fc62121df3ccdeed8c7bb0919127dc1ff4b",
                "12462dea26d2038d06d19d7154251595de503e912b5a22490a03d2571265b773",
                "4f421694fab048f78347814d325f867e638b884669c6de0ec5944068e78f9ad0",
                "19d935774eb333911c8a2534689c3f28b115c9b1cc6fda121fca7ca597d5e5c6",
                "44d8dfeec83481f5a952e21c9dbc6f53e71ec4988c10b8dd48c21764d28bcc18",
                "f23b94b69eefb41d0e6974d7a67888954d9028fd71a4c87a66d93fc2add7a7ee",
                "bc567cd65178804afad13ed87d4d14b97bc2818c1f3d8b4ffcc854e826500131",
                "f9072385bf4afee849fde609b4917f2266764a378b9bfb2e27da6e1ff8a438be",
                "5690821732e6e2a0bb64865fcd817a2cad764e6844954de04cad66a22372cbe7",
                "1980e4bb3e8339c1baf7cf3fe80cf7d1b426d13cd60604d3f9a16bb8740de0bc",
                "b154c56d088bb0e11800284b15be8bd56774f0c86a928901a7d82262765d0a9a",
                "a507e73f73f49a481ab65545140e03426887e648774dc28d4a099ed8bb5ad341",
                "ab14c53cfc83adbd50bb90edcbac08cea341a48975f95d1c9d1cfbd678b2685c",
                "8b2088caf1a2f192043111d51499b378f4bb8963e9490149a242ed25e7d17f5b",
                "88d2ad6e5a01465cc759b3ecfc548d62554b6a376973c5ea4050c4fa619d616d",
                "126cc4315b36cee44d17348244038425e865ae094c6ccb6d8806b6a183515fbc",
                "51c94ca34736b10f36dea6a63710478c368eb6a84a0e4b6404708e1b965ed331",
                "3b415d376f4b4d03842a8ecb72bef6d786285c8e7cfe9312f55a0de7d1c97df1",
                "82f3d3031904e8dba24087b5ca07a3e6b042865cbdec88694d99f93f1977f214",
                "1d3fc98881fb59be3fe0c6f582519f63a1b042bbb18edd1e4b7114cf45312bc5",
                "73a4aeaaf6ef402a485bdf26c8409189db8a8428721e341c4cea2daaa7e3d022",
                "051a6bd44f467bdbb6232c6425783662e4b33ad6daa155c1182e0dd827f4d947",
                "5a909a547394e9706dd7546641b790d9ba33bd3841f30192e643352cbdb2155a",
                "19da6ae173a1746ab501faa2a42ad68689330cf28a3bb341b56a06beb4eeb55e",
                "3706c1c333f0bc92d08e91b694842d3d53658f32edb5676475ddf90f90979ae1",
                "8d95608ca144420c6507d33e55acd52388144bd379c9b7873e398395e291c731",
                "0458f20267dbd8f05450b87186e213983dfe611f5a989992cf5ecc01696bca15",
                "17c529e538ce83a0b7ddb361e099fa8cdead683fc0d7887613d0e65de3656068",
                "59db62de6945017ebdd4059b1c6be5e8c85c1cdfff933da24a6818061252de3e",
                "fbab23758b26c0ddc0150bd6f0265a40f15321fdc2d1086981530ff7bb68e290",
                "2f3794b8c15b8907690725e969ca48d3c2c3b4cf6e5cb30ddf085ea532de6e35"
              ],
              "utxo": [
                {
                  "block_id":641069,
                  "transaction_hash":"b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                  "index":94,
                  "value":15000030000
                },
                {
                  "block_id":641057,
                  "transaction_hash":"cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                  "index":2,
                  "value":785000000000
                }
              ]
            }
          },
          "context": {
            "code":200,
            "source":"D",
            "limit":"100,100",
            "offset":"0,0",
            "results":1,
            "state":641187,
            "cache": {
              "live":false,
              "duration":30,
              "since":"2020-07-28 15:30:07",
              "until":"2020-07-28 15:30:37",
              "time":5.9604644775390625e-6
            },
            "api": {
              "version":"2.0.64",
              "last_major_update":"2020-07-19 00:00:00",
              "next_major_update":null,
              "documentation":"https://blockchair.com/api/docs",
              "notice":"Beginning July 19th, 2020 we start enforcing request cost formulas, see the changelog for details"
            },
            "time":1.5537691116333008,
            "render_time":0.01607990264892578,
            "full_time":0.01608586311340332,
            "request_cost":1
          }
        } 
      }
      this.resquest_data = response.data.data[Object.keys(response.data.data)]
      this.adress_info = this.resquest_data.adress
      this.transactions = this.resquest_data.transactions
      this.last_transactions = this.transactions.slice(0, 10)
      this.utxo = this.resquest_data.utxo
      this.valid_adress = true

      // True API call
      // let path = 'https://api.blockchair.com/' + this.coin_type + '/dashboards/address/' + this.adress
      // this.axios
      //   .get(path)
      //   .then((response) => {
        //     if (response.status != 200) {
          //       alert("Something went wrong\nStatus " + response.status)
      //     } else {
        //       this.resquest_data = response.data.data[Object.keys(response.data.data)]
      //       this.adress_info = this.resquest_data.adress
      //       this.transactions = this.resquest_data.transactions
      //       this.last_transactions = this.transactions.slice(0, 10)
      //       this.utxo = this.resquest_data.utxo
      //       this.valid_adress = true
      //     }
      //   })
      
    },
    get_transactions_info: function() {
      let response = {
        "data": {
          "data": {
            "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178": {
              "transaction": {
                "block_id": 641069,
                "id": 552663434,
                "hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                "date": "2020-07-27",
                "time": "2020-07-27 17:58:48",
                "size": 3870,
                "weight": 15144,
                "version": 2,
                "lock_time": 641068,
                "is_coinbase": false,
                "has_witness": true,
                "input_count": 4,
                "output_count": 100,
                "input_total": 19681259020,
                "input_total_usd": 1952440,
                "output_total": 19680880020,
                "output_total_usd": 1952410,
                "fee": 379000,
                "fee_usd": 37.598,
                "fee_per_kb": 97932.8,
                "fee_per_kb_usd": 9.71525,
                "fee_per_kwu": 25026.4,
                "fee_per_kwu_usd": 2.4827,
                "cdd_total": 115.72713504733,
                "is_rbf": false
              },
              "inputs": [
                {
                  "block_id": 641068,
                  "transaction_id": 552661549,
                  "index": 60,
                  "transaction_hash": "16cf3644b40488217af0cffcaac435ff58053c4f245b823ed54ce1a08db0bf13",
                  "date": "2020-07-27",
                  "time": "2020-07-27 17:48:38",
                  "value": 1602208,
                  "value_usd": 158.944,
                  "recipient": "bc1qa3hd7c2vqdxeqfuqvjq3fy6gclsdh73uhf2vmc",
                  "type": "witness_v0_keyhash",
                  "script_hex": "0014ec6edf614c034d9027806481149348c7e0dbfa3c",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641069,
                  "spending_transaction_id": 552663434,
                  "spending_index": 0,
                  "spending_transaction_hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 17:58:48",
                  "spending_value_usd": 158.944,
                  "spending_sequence": 4294967294,
                  "spending_signature_hex": "",
                  "spending_witness": "3044022010743c70119463fc0d2e350e71d9da2b3a61a1a8340b5748579779d311241c9c022052fc42f35c8c3c4208f68116289ce748b895c6a89043421f4b5c66cc207b67e601,03d21f9aefdf9a9257a96f673dd45632270faf3910cb6c12ef3965305f5c453c3a",
                  "lifespan": 610,
                  "cdd": 0
                },
                {
                  "block_id": 641058,
                  "transaction_id": 552638226,
                  "index": 0,
                  "transaction_hash": "daea4b411d65aa1aae699d618a89db43f5da5d087596fbe63e6eac63881bfd21",
                  "date": "2020-07-27",
                  "time": "2020-07-27 16:40:31",
                  "value": 10000000000,
                  "value_usd": 992032,
                  "recipient": "1NDyJtNTjmwk5xPNhjgAMu4HDHigtobu1s",
                  "type": "pubkeyhash",
                  "script_hex": "76a914e8cea30989bd15530f819b766684b00dc7ba7cfa88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641069,
                  "spending_transaction_id": 552663434,
                  "spending_index": 1,
                  "spending_transaction_hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 17:58:48",
                  "spending_value_usd": 992032,
                  "spending_sequence": 4294967294,
                  "spending_signature_hex": "4730440220733bf4ac680e7a7d39f063c578fc0e6816e2f2bb16d4fd983680a580070c8db502200677ce38b7ff934ff19814dfe8ca56b0e0097fe03d248a913852a59d6a848b5a012102679a681d9b5bf5c672e0413997762664a17009038674b806bf27dd6b368d9b67",
                  "spending_witness": "",
                  "lifespan": 4697,
                  "cdd": 5.43634259259259
                },
                {
                  "block_id": 641026,
                  "transaction_id": 552561236,
                  "index": 1,
                  "transaction_hash": "7bef3bee245832ce04172ff9dc2b5bb65ced33d5fa0fdee0342db3cf6474d55d",
                  "date": "2020-07-27",
                  "time": "2020-07-27 12:20:14",
                  "value": 749900507,
                  "value_usd": 74392.5,
                  "recipient": "1NDyJtNTjmwk5xPNhjgAMu4HDHigtobu1s",
                  "type": "pubkeyhash",
                  "script_hex": "76a914e8cea30989bd15530f819b766684b00dc7ba7cfa88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641069,
                  "spending_transaction_id": 552663434,
                  "spending_index": 2,
                  "spending_transaction_hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 17:58:48",
                  "spending_value_usd": 74392.5,
                  "spending_sequence": 4294967294,
                  "spending_signature_hex": "47304402206b015765b08fdc80c02136832b5decf48eba82853c776487225df04464efb66302202c306881d03f1ab97dbc899a4f71cf03e56da888c2a8823ec72d1b0402325381012102679a681d9b5bf5c672e0413997762664a17009038674b806bf27dd6b368d9b67",
                  "spending_witness": "",
                  "lifespan": 20314,
                  "cdd": 1.64581018518519
                },
                {
                    "block_id": 640876,
                    "transaction_id": 552254019,
                    "index": 0,
                    "transaction_hash": "e1330bd7f884d721eb9725f3b239cfd2b6d286d4200415cd6ddd34a78f4d6773",
                    "date": "2020-07-26",
                    "time": "2020-07-26 12:48:42",
                    "value": 8929756305,
                    "value_usd": 864337,
                    "recipient": "1NDyJtNTjmwk5xPNhjgAMu4HDHigtobu1s",
                    "type": "pubkeyhash",
                    "script_hex": "76a914e8cea30989bd15530f819b766684b00dc7ba7cfa88ac",
                    "is_from_coinbase": false,
                    "is_spendable": null,
                    "is_spent": true,
                    "spending_block_id": 641069,
                    "spending_transaction_id": 552663434,
                    "spending_index": 3,
                    "spending_transaction_hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                    "spending_date": "2020-07-27",
                    "spending_time": "2020-07-27 17:58:48",
                    "spending_value_usd": 885860,
                    "spending_sequence": 4294967294,
                    "spending_signature_hex": "4730440220430959a8d1c6a47ea7a0574d75afd9a3d576842cbd5ae52c8a238c2e6fe963230220652107d6d35f351ba58b05e9717851c1ee7a251823fcd9a0a3ae391520bcefd7012102679a681d9b5bf5c672e0413997762664a17009038674b806bf27dd6b368d9b67",
                    "spending_witness": "",
                    "lifespan": 105006,
                    "cdd": 108.165902777778
                }
              ],
              "outputs": [
                {
                  "block_id": 641069,
                  "transaction_id": 552663434,
                  "index": 0,
                  "transaction_hash": "b2ccb01f4aa819ad370f146ef49ade3f8b1aaff1620dbc6c47a35d39ed55e178",
                  "date": "2020-07-27",
                  "time": "2020-07-27 17:58:48",
                  "value": 636675,
                  "value_usd": 63.1602,
                  "recipient": "1PhKgj7a8tGjag1Gpzh9Sd6F2gGUtU8Qvb",
                  "type": "pubkeyhash",
                  "script_hex": "76a914f8f300cbe0efcc2b861a2c1c8eea0e8eba16959888ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": false,
                  "spending_block_id": null,
                  "spending_transaction_id": null,
                  "spending_index": null,
                  "spending_transaction_hash": null,
                  "spending_date": null,
                  "spending_time": null,
                  "spending_value_usd": null,
                  "spending_sequence": null,
                  "spending_signature_hex": null,
                  "spending_witness": null,
                  "lifespan": null,
                  "cdd": null
                }
              ]
            },
            "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c": {
              "transaction": {
                "block_id": 641057,
                "id": 552636404,
                "hash": "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                "date": "2020-07-27",
                "time": "2020-07-27 16:40:36",
                "size": 679,
                "weight": 2716,
                "version": 2,
                "lock_time": 0,
                "is_coinbase": false,
                "has_witness": false,
                "input_count": 3,
                "output_count": 4,
                "input_total": 818290903605,
                "input_total_usd": 81177100,
                "output_total": 818290850000,
                "output_total_usd": 81177100,
                "fee": 53605,
                "fee_usd": 5.31779,
                "fee_per_kb": 78947,
                "fee_per_kb_usd": 7.83179,
                "fee_per_kwu": 19736.7,
                "fee_per_kwu_usd": 1.95795,
                "cdd_total": 6551.2426794245,
                "is_rbf": false
              },
              "inputs": [
                {
                  "block_id": 640977,
                  "transaction_id": 552451525,
                  "index": 4,
                  "transaction_hash": "f23dafd04481ca688d355bae1dc3d31acbe97b3108da1fe40f6406e92025d01d",
                  "date": "2020-07-27",
                  "time": "2020-07-27 03:53:29",
                  "value": 41195903605,
                  "value_usd": 4086770,
                  "recipient": "1KFHE7w8BhaENAswwryaoccDb6qcT6DbYY",
                  "type": "pubkeyhash",
                  "script_hex": "76a914c825a1ecf2a6830c4401620c3a16f1995057c2ab88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641057,
                  "spending_transaction_id": 552636404,
                  "spending_index": 0,
                  "spending_transaction_hash": "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 16:40:36",
                  "spending_value_usd": 4086770,
                  "spending_sequence": 4294967295,
                  "spending_signature_hex": "473044022042bd2e4fec1f03cc9f890888342c3423aaf3e31cfa94fd6008ba3115bb21ebc4022034e035a4285482a5d3a015333692edeac9bf9de05b335ccda7019eb5d7ef781c014104e7e8eeb1d060e2ae611e2e6253b7948d7c02b7ea7c2dce09d939225a5c39d86553b07acf5073b1dc1e432cdf574d587b2800e0c3d4e43fcb3a1f84bfdf602a1e",
                  "spending_witness": "",
                  "lifespan": 46027,
                  "cdd": 218.947881944444
                },
                {
                  "block_id": 640930,
                  "transaction_id": 552373863,
                  "index": 0,
                  "transaction_hash": "45dfaaa77a6f45bdf9a0e9b50f784badfc0ae19a1a17a1eaadf59b3f8b9bc119",
                  "date": "2020-07-26",
                  "time": "2020-07-26 20:57:02",
                  "value": 770000000000,
                  "value_usd": 74530500,
                  "recipient": "1J1F3U7gHrCjsEsRimDJ3oYBiV24wA8FuV",
                  "type": "pubkeyhash",
                  "script_hex": "76a914ba85dc466140d3ef2eac3f7e42088ec501315a4b88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641057,
                  "spending_transaction_id": 552636404,
                  "spending_index": 1,
                  "spending_transaction_hash": "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 16:40:36",
                  "spending_value_usd": 76386500,
                  "spending_sequence": 4294967295,
                  "spending_signature_hex": "47304402206fadf21e006bdcd15161a9dba58fb16625c74318148d30acbefb1dafe5129c56022010474b027d9fedc95885f44d9ddaaf694b53f631d6f48938d9b9c8fb1d5cc13e014104054f0d458c4dc3d0a4bb35cd17e624eb76ea99b702561bd0bea0aefe34c6c860fafca4faae957bb009e0ece9cba07cccd30dc008512a9a3021dbcfd2127938fc",
                  "spending_witness": "",
                  "lifespan": 71014,
                  "cdd": 6328.79398148148
                },
                {
                  "block_id": 641049,
                  "transaction_id": 552617879,
                  "index": 94,
                  "transaction_hash": "1a82b98fd2eeb8917b4c83ed8690219efea6e0353681768099f049763a99e87f",
                  "date": "2020-07-27",
                  "time": "2020-07-27 15:39:55",
                  "value": 7095000000,
                  "value_usd": 703847,
                  "recipient": "1J1F3U7gHrCjsEsRimDJ3oYBiV24wA8FuV",
                  "type": "pubkeyhash",
                  "script_hex": "76a914ba85dc466140d3ef2eac3f7e42088ec501315a4b88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641057,
                  "spending_transaction_id": 552636404,
                  "spending_index": 2,
                  "spending_transaction_hash": "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                  "spending_date": "2020-07-27",
                  "spending_time": "2020-07-27 16:40:36",
                  "spending_value_usd": 703847,
                  "spending_sequence": 4294967295,
                  "spending_signature_hex": "4730440220645e2bf81662a5def781cc67920e115ac16a593e792deaafeb95743a807412cf02205d4be58728de410231340350958cfb490174326d0e362679c3372f82c89cc58c014104054f0d458c4dc3d0a4bb35cd17e624eb76ea99b702561bd0bea0aefe34c6c860fafca4faae957bb009e0ece9cba07cccd30dc008512a9a3021dbcfd2127938fc",
                  "spending_witness": "",
                  "lifespan": 3641,
                  "cdd": 2.94988425925926
                }
              ],
              "outputs": [
                {
                  "block_id": 641057,
                  "transaction_id": 552636404,
                  "index": 0,
                  "transaction_hash": "cb835ef0a7283311b309e1241dc94dd9cca95d534d20309cb985f1950ce3984c",
                  "date": "2020-07-27",
                  "time": "2020-07-27 16:40:36",
                  "value": 24195850000,
                  "value_usd": 2400310,
                  "recipient": "1KFHE7w8BhaENAswwryaoccDb6qcT6DbYY",
                  "type": "pubkeyhash",
                  "script_hex": "76a914c825a1ecf2a6830c4401620c3a16f1995057c2ab88ac",
                  "is_from_coinbase": false,
                  "is_spendable": null,
                  "is_spent": true,
                  "spending_block_id": 641131,
                  "spending_transaction_id": 552807499,
                  "spending_index": 15,
                  "spending_transaction_hash": "ceee0140bf550e4c2509ccfde89e5709ac23e43940422e3ef538429ca1d81e64",
                  "spending_date": "2020-07-28",
                  "spending_time": "2020-07-28 04:26:26",
                  "spending_value_usd": 2707360,
                  "spending_sequence": 4294967295,
                  "spending_signature_hex": "4730440220287899a4acd3ad827350c6b35455f6f7302a9e4e864bce3769d6ce9d4bf591cb0220712b5bd0ad6d3d2a655e093f732d0ad7d6ca37be92735dd1156ea7e8663440c6014104e7e8eeb1d060e2ae611e2e6253b7948d7c02b7ea7c2dce09d939225a5c39d86553b07acf5073b1dc1e432cdf574d587b2800e0c3d4e43fcb3a1f84bfdf602a1e",
                  "spending_witness": "",
                  "lifespan": 42350,
                  "cdd": 118.129050925926
                }
              ]
            }
          },
          "context": {
            "code": 200,
            "source": "D",
            "results": 4,
            "state": 641190,
            "cache": {
              "live": true,
              "duration": 60,
              "since": "2020-07-28 15:54:12",
              "until": "2020-07-28 15:55:12",
              "time": null
            },
            "api": {
              "version": "2.0.64",
              "last_major_update": "2020-07-19 00:00:00",
              "next_major_update": null,
              "documentation": "https://blockchair.com/api/docs",
              "notice": "Beginning July 19th, 2020 we start enforcing request cost formulas, see the changelog for details"
            },
            "time": 0.17992091178894043,
            "render_time": 0.059609174728393555,
            "full_time": 0.23953008651733398,
            "request_cost": 1.3
          }
        }
      }
      this.transactions_details = response.data.data
    },
    isValidHttpUrl: function(string) {
      let url;

      try {
        url = new URL(string);
      } catch (_) {
        return false;  
      }

      return url.protocol === "http:" || url.protocol === "https:";
    }
  },
  components: {
    TransactionRecord
  }
}
</script>

<style scoped>
</style>