<template>
    <div class="containerbody">
        <div class="searchchord" id="searchchord">
            <h2>コード検索</h2>
            <div class="chordcon">
                <div class="selectchord">
                    <select v-model="chord" v-on:change="showchord">
                        <option v-for="(value,key) in chordlist" v-bind:key="key">{{key}}</option>
                    </select>
                </div>
                <div class="showchord">
                    <p v-for="(chordmem,key) in msgchord" v-bind:key="key"><span>{{chordmem.name}}</span></p>
                </div>
            </div>
        </div>
        <div class="createchord" id="createchord">
            <h2>コード作成</h2>
            <div class="chordcon">
                <div class="insertchord">
                <span>{{count}}小節目に</span>
                    <textarea name="" id="" cols="16" rows="1" v-model="mychord"></textarea>
                    <button @click="addChord(mychord)" class="addchord">追加する</button>
                </div>
                <div class="deletechord">
                    <textarea name="" id="" cols="3" rows="1" v-model="bar"></textarea>
                    <span>小節目を</span>
                    <button @click="delChord(bar)" class="delchord">削除する</button>
                </div>
                <div class="changechord">
                    <textarea name="" id="" cols="3" rows="1" v-model="changebar"></textarea>
                    <span>小節目を</span>
                    <textarea name="" id="" cols="16" rows="1" v-model="changechord"></textarea>に
                    <button @click="chaChord(changebar,changechord)" class="delchord">変更する</button>
                </div>
                <p>作成したコード</p>
                <div class="result" v-for="(item,index) in makechord" v-bind:key="index">第{{index + 1}}小節目 {{item}}</div>
            </div>
        </div>
        <div class="showmychord" id="showmy">
            <h2>コード表示</h2>
            <p>登録したコードを表示する</p>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            chord:'',
            chordlist:{
                C:[{name:'C '},
                {name:'Dm '},
                {name:'Em '},
                {name:'F '},
                {name:'G '},
                {name:'Am '},
                {name:'Bm(♭5)'},
                ],
                D:[{name:'D '},
                {name:'Em '},
                {name:'F#m '},
                {name:'G '},
                {name:'A '},
                {name:'Bm '},
                {name:'C#m(♭5)'},
                ],
                E:[{name:'E '},
                {name:'F#m '},
                {name:'G#m '},
                {name:'A '},
                {name:'B '},
                {name:'C#m '},
                {name:'D#m(♭5)'},
                ],
                F:[{name:'F '},
                {name:'Gm '},
                {name:'Am '},
                {name:'B♭ '},
                {name:'C '},
                {name:'Dm '},
                {name:'Em(♭5)'},
                ],
                G:[{name:'G '},
                {name:'Am '},
                {name:'Bm '},
                {name:'C '},
                {name:'D '},
                {name:'Em '},
                {name:'F#m(♭5)'},
                ],
                A:[{name:'A '},
                {name:'Bm '},
                {name:'C#m '},
                {name:'D '},
                {name:'E '},
                {name:'F#m '},
                {name:'G#m(♭5)'},
                ],
                B:[{name:'B '},
                {name:'C#m '},
                {name:'D#m '},
                {name:'E '},
                {name:'F# '},
                {name:'G#m '},
                {name:'A#m(♭5)'},
                ],
                Cm:[{name:'Cm '},
                {name:'Dm(♭5) '},
                {name:'E♭m '},
                {name:'F#m '},
                {name:'G#m '},
                {name:'A♭ '},
                {name:'B♭'},
                ],
                Dm:[{name:'Dm '},
                {name:'Em(♭5) '},
                {name:'Fm '},
                {name:'Gm '},
                {name:'Am '},
                {name:'B♭ '},
                {name:'C'},
                ],
                Em:[{name:'Em '},
                {name:'F#m(♭5) '},
                {name:'G '},
                {name:'Am '},
                {name:'Bm '},
                {name:'C '},
                {name:'D'},
                ],
                Fm:[{name:'Fm '},
                {name:'Gm(♭5) '},
                {name:'A♭ '},
                {name:'B♭m '},
                {name:'Cm '},
                {name:'D♭ '},
                {name:'E♭'},
                ],
                Gm:[{name:'Gm '},
                {name:'Am(♭5) '},
                {name:'B♭ '},
                {name:'Cm '},
                {name:'Dm '},
                {name:'E♭ '},
                {name:'F'},
                ],
                Am:[{name:'Am '},
                {name:'Bm(♭5) '},
                {name:'C '},
                {name:'Dm '},
                {name:'Em '},
                {name:'F '},
                {name:'G'},
                ],
                Bm:[{name:'Bm '},
                {name:'C#m(♭5) '},
                {name:'D '},
                {name:'Em '},
                {name:'F#m '},
                {name:'G '},
                {name:'A'},
                ],
            },
            msgchord: '',
            mychord:'',
            makechord:[],
            count:1,
            bar:'',
            barcount:'',
            changebar:'',
            changechord:'',
        }
    },
    methods:{
        showchord(){
            this.msgchord = this.chordlist[this.chord];
        },
        addChord(item){
            // 表示用コードの追加
            this.makechord.push(item);
            // ボタン押下後にテキストを空にする
            this.mychord = '';
            // 小節数のカウント
            this.count = this.count + 1;
        },
        delChord(barc){
            this.barcount = Number(barc) - 1;
            this.makechord.splice(this.barcount,1);
            this.bar = '';
            this.count = this.count - 1;
        },
        chaChord(bar,chord){
            this.barcount = Number(bar) -1;
            this.$set(this.makechord,this.barcount, chord);
            this.changebar = '';
            this.changechord = '';
        },
    }
}
</script>

<style scoped>
p{
    display: inline-block;
}
span{
    margin-right: 10px;
}
.containerbody{
    height: 100%;
    width: 900px;
    margin: auto;
}
.searchchord{
    height: 150px;
}
.chordcon{
    width: 800px;
    margin: auto;
}
.insertchord{
    height: 50px;
    width: 100%;
}
.deletechord{
    height: 50px;
    width: 100%;
}
.changechord{
    height: 50px;
    width: 100%;
}
.result{
    background-color: aliceblue;
}
</style>