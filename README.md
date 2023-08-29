import 'package:task_9/task_9.dart' as task_9;


//   class Car{
//   int speed;
//   String color;
//   String owner;
//   String name;
//   Car({ required this.name,required this.color,required this.owner,required this.speed}) {}
//   void speedup(){
//     speed+=15;
//   }
//   void brake(){
//     speed-=15;
//   }
//   void info() {
//     print("My name is $owner, my car is $name, it is $color, and I am driving at $speed now");
//   }
//   }
//   class Bmw extends Car{
//     Bmw({required String color,required String owner, required int speed}) :
//           super(name: 'bmw', color: color, owner: owner, speed: speed){}
//     void speedup(){
//       speed+=30;
//     }
//     void brake(){
//       speed-=30;
//     }
//     void info(){
//       print("My name is $owner, my car is $name, it is $color, and I am driving at $speed now");
//     }
//   }
//   class Toyata extends Car{
//     Toyata({required super.color, required super.owner,required super.speed}):super(name: "toyota"){}
//     void speedup(){
//       speed+=20;
//     }
//     void brake(){
//       speed-=20;
//     }
//     void info(){
//       print("My name is $owner, my car is $name, it is $color, and I am driving at $speed now");
//     }
//   }
// void main(){
//     Car car0=Car(name: "honda", color: "red", owner: "ahmedd", speed: 100);
//     Bmw car1=Bmw(color: "black", owner: "ahmed", speed: 190);
//     Toyata car2=Toyata(color: "black", owner: "ahmed", speed: 90);
//     car0.speedup();
//     car0.info();
//     print("--------------------------------------------");
//     car1.brake();
//     car1.info();
//     print("--------------------------------------------");
//     car2.speedup();
//     car2.info();
//   }
class Player{
  int age;
  String name;
  String place;
  Player({required this.age,required this.name,required this.place}){}

}
class attackPlayer extends Player{
  int numberGoals;
    attackPlayer({required this.numberGoals,required super.age,required super.name,required super.place}){}
}
class defenderPlayer extends Player{
  int numberAssist;
  defenderPlayer({required this.numberAssist,required super.age,required super.name,required super.place}){}
}
class goalkeeperPlayer extends Player{
  int cleansheet;
  goalkeeperPlayer({required this.cleansheet,required super.age,required super.name,required super.place}){}

}
class Team {
  String Trainer;
  List<attackPlayer> attacks;
  List<defenderPlayer> defenders;
  List<goalkeeperPlayer> goalkeepers;
  Team({required this.Trainer, required this.attacks, required this.defenders, required this.goalkeepers}); //constructor

  void addPlayer(Player p) {
    if (p is attackPlayer && p.age > 18 && p.age < 30 && p.place == "attack") {
      attacks.add(p);
    } else if (p is defenderPlayer && p.age > 18 && p.age < 30 &&
        p.place == "defender") {
      defenders.add(p);
    } else if (p is goalkeeperPlayer && p.age > 18 && p.age < 30 &&
        p.place == "goalkeeper") {
      goalkeepers.add(p);
    }
  }  //method add player
void info(){
  print("\nTeam Info:");
  print("Trainer: ${Trainer}");
  for (var attacker in attacks){
    print("name : ${attacker.name}\n"
        "age : ${attacker.age}\n"
        "place : ${attacker.place}\n"
        "number of goals : ${attacker.numberGoals}");
  }
  for (var deffender in defenders){
    print("name : ${deffender.name}\n"
        "age : ${deffender.age}\n"
        "place : ${deffender.place}\n"
        "number of goals : ${deffender.numberAssist}");
  }
  for (var goalkepper in goalkeepers){
    print("name : ${goalkepper.name}\n"
        "age : ${goalkepper.age}\n"
        "place : ${goalkepper.place}\n"
        "number of goals : ${goalkepper.cleansheet}");
  }
}
}
void main() {
   attackPlayer attacker1 = attackPlayer(age: 25, name: "ahmed", place: "attack", numberGoals: 15);              //create var from attackplayer
  defenderPlayer defender1 = defenderPlayer(age: 28, name: "mohamed", place: "defender", numberAssist: 10);        //
   goalkeeperPlayer goalkeeper1 = goalkeeperPlayer(age: 30, name: "mostafa", place: "goalkeeper", cleansheet: 8);   //

  List<attackPlayer> attackPlayers = [attacker1];   //create list
  List<defenderPlayer> defenderPlayers = [defender1];
  List<goalkeeperPlayer> goalkeeperPlayers = [goalkeeper1];

  Team myTeam = Team(
    Trainer: "beb",
    attacks: attackPlayers,
    defenders: defenderPlayers,
    goalkeepers: goalkeeperPlayers,
  );
  attackPlayer newAttacker = attackPlayer(age: 22, name: "joe", place: "attack", numberGoals: 5);
  myTeam.addPlayer(newAttacker);    //add newplayer
  defenderPlayer def2=defenderPlayer(numberAssist: 4, age: 22, name: "mo", place: "defender");
  myTeam.addPlayer(def2);    //add  newplayer

  myTeam.info();
}

