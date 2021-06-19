# Sr-julius

import { StatusBar } from 'expo-status-bar';
import React,{useState} from 'react';
import { StyleSheet, Text, View, TextInput, TouchableOpacity, Image, ImageBackground} from 'react-native';
import C1 from './componentes/comp1'


export default function app() {

  const img = './assets/imgs/img3.png'

  const[r,setR]=useState(0)
  const[n,setN]=useState(0)

  function calcular(){  

    var numeroinicial = n
    var i = 0
    var cont = 0
    var valor = []
    
    while (i!= 1)
    {
      if (numeroinicial%2==0)
      {
        valor[cont] = 0
        numeroinicial = Math.floor(numeroinicial/2)
        cont +=1
      }if (numeroinicial%2==1)
      {
        valor[cont] = 1
        numeroinicial = Math.floor(numeroinicial/2)
        cont +=1
      }
      if(numeroinicial == 1){
        valor[cont] = 1
        i = 1
      }if(numeroinicial == 0)
      {
        i = 1
      }
    }
    valor.reverse()
    setR(valor)
  }

  return (
    <View style={styles.container}>
      <ImageBackground
      source={require(img)}
      style={styles.bgimg}
      >
      
      <View style={styles.caixa}>
      <Text style={styles.titulo}>Transformação em Binário:</Text>
      <Image source={require("./assets/imgs/img1.png")} style={styles.logo}/>
      <TextInput style={styles.input}
       placeholder='Digite o valor'
        keyboardType='numeric'
        onChangeText={text=>setN(text)}
        />
         <View style={styles.result}>
      <TouchableOpacity style={styles.bt} onPress={() => calcular()}><Text style={styles.bttext}>Gerar</Text></TouchableOpacity>
      </View>
      <Text style={styles.txtresp}>{r}</Text>
      </View>
      </ImageBackground>
    </View>
    
  );
}


const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#0ff',
    alignItems: 'center',
    justifyContent: 'center',

  },

  bgimg:{
    flex:1,
    resizeMode:'cover',
    width:'100%',
  },

  img:{
    flex: 1,
    resizeMode: "cover",
    width:'100%',
  },

  caixa:{
    flex:1,
    marginBottom: 10,
    alignItems:'center',
    justifyContent:'center',
  },

  logo:{
    width: 100,
    height: 100,
    marginBottom:50,
  },

  titulo:{
    fontSize: 21,
    padding: 10,
    borderStyle: "dotted",
    fontWeight: '700',
    color:'#0aff',
    marginBottom:20,
  },

  input:{
    height: 60,
    width: 250,
    fontSize: 25,
    marginBottom: 30,
    backgroundColor:'#fff',
    borderRadius:10,
  },

  bt:{
    height: 50,
    width: 120,
    borderRadius: 10,
    fontSize: 50,
    alignItems:'center',
    backgroundColor:'#aff',
    marginBottom:30,
  },

  bttext:{
    fontSize:30,
    color:'#000',
  },

  result:{
    marginTop:10,
  },

  txtresp:
  {
    color:'#000',
    fontSize: 30,
  },
});
