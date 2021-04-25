import 'package:flutter/material.dart';

class Result extends StatelessWidget {
  final int resultScore;
  final Function resetHandler;

  Result(this.resultScore, this.resetHandler);

  String get resultPhrase {
    String resultText;
    if (resultScore >= 9) {
      resultText = "You are most Aware.";
    } else if (resultScore >= 7) {
      resultText = "You are much Aware. \n Keep going on.";
    } else if (resultScore >= 5) {
      resultText = "You are just Aware.  \n Lets read more about Corona Virus.";
    } else if (resultScore >= 3) {
      resultText =
          "You are not so Aware. \n Plz study more about Corona Virus. ";
    } else if (resultScore >= 1) {
      resultText = "You are not at all Aware. \n You are in Danger.";
    } else {
      resultText =
          "No Comments. \n It seems as if you don't even know about it.";
    }
    return resultText;
  }

  @override
  Widget build(BuildContext context) {
    return Align(
      alignment: Alignment.center,
      child: Column(
        children: <Widget>[
          Text(
            resultPhrase,
            style: TextStyle(fontSize: 36, fontWeight: FontWeight.bold),
            textAlign: TextAlign.center,
          ),
          // ignore: deprecated_member_use
          FlatButton(
            child: Text(
              'Restart Quiz!!!',
              style: TextStyle(fontSize: 20),
              textAlign: TextAlign.center,
            ),
            textColor: Colors.blue,
            onPressed: resetHandler,
          ),
        ],
      ),
    );
  }
}
