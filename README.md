# React native async storage

Created by Vishnugupta Chanakya(irshad) 

App.js 
async storage is used to save data locally. in android it uses shared preferences and ios it uses UserDefaults

            import React, {Component} from 'react';
            import {Platform, StyleSheet, Text, View, AsyncStorage, TextInput,Button} from 'react-native';

            export default class App extends Component {

            constructor(){
                super()
                this.state = {
                names: "No data"

                }
            }
            render() {
                return (
                <View style={styles.container}>

                    <TextInput placeholder="Enter something" value={this.state.names} underlineColorAndroid="#FF0000" />
                    <Button title="Save" onPress={this.onPress}/>
                    <Button title="display" onPress={this.displayData}/>

                    <Text>{this.state.names}</Text>
                </View>
                );
            }
            onPress(){
            let user = "Vishnugupta Chanakya";

            let obj = {
            name: 'Vishnugupta Chanakya 2',
            email: 'vishnu@gmail.com 2',
            city: 'Shimoga 2'
            }
            AsyncStorage.setItem('user',JSON.stringify(obj));

            }

            displayData = async () => {
            try{
            let user = await AsyncStorage.getItem('user');
            let parsed  = JSON.parse(user);
            alert(parsed.name)
            this.setState({
            names: parsed.name

            }) 
            }catch(error){
            alert(error)
            }
            }
            }


            const styles = StyleSheet.create({
            container: {
                flex: 1,
                justifyContent: 'center',
                alignItems: 'center',
                backgroundColor: '#F5FCFF',
            },
            welcome: {
                fontSize: 20,
                textAlign: 'center',
                margin: 10,
            },
            instructions: {
                textAlign: 'center',
                color: '#333333',
                marginBottom: 5,
            },
            });


