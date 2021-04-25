import 'package:flutter/material.dart';

import './quiz.dart';
import './result.dart';

void main() => runApp(MyApp());

class MyApp extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return _MyAppState();
  }
}

class _MyAppState extends State<MyApp> {
  final _questions = const [
    {
      'questionText':
          'The first case of novel coronavirus was identified in ..... ',
      'answers': [
        {'text': 'A. Beijing', 'score': 0},
        {'text': 'B. Shanghai', 'score:': 0},
        {'text': 'C. Wuhan, Hubei ', 'score': 1},
        {'text': 'D. Tianjin', 'score': 0},
      ],
    },
    {
      'questionText':
          'World Health Organisation on 11 February, 2020 announced an official name for the disease that is causing the 2019 novel coronavirus outbreak? What is the new name of the disease?',
      'answers': [
        {'text': 'A. COVID-19', 'score': 1},
        {'text': 'B. COVn-19', 'score:': 0},
        {'text': 'C. COnV-20', 'score': 0},
        {'text': 'D. COnVID-19', 'score': 0},
      ],
    },
    {
      'questionText': 'Mild Symptoms of Novel coronavirus are:',
      'answers': [
        {'text': 'A. Fever', 'score': 0},
        {'text': 'B. Cough', 'score:': 0},
        {'text': 'C. Shortness of breath', 'score': 0},
        {'text': 'D. All of the above', 'score': 1},
      ],
    },
    {
      'questionText':
          'It is recommended that you wash your hands for at least______of time.',
      'answers': [
        {'text': 'A. 10 seconds', 'score': 0},
        {'text': 'B. 5 seconds', 'score': 0},
        {'text': 'C. 20 seconds', 'score': 1},
        {'text': 'D. 5 minutes', 'score': 0},
      ],
    },
    {
      'questionText': 'From where did coronavirus got its name?',
      'answers': [
        {'text': 'A. Due to their crown-like projections.', 'score': 1},
        {'text': 'B. Due to their leaf-like projections.', 'score': 0},
        {'text': 'C. Due to their surface structure of bricks.', 'score': 0},
        {'text': 'D. None of the above', 'score': 0},
      ],
    },
    {
      'questionText': 'How is COVID-19 passed on?',
      'answers': [
        {
          'text':
              'A. Through droplets that come from your mouth and nose when you cough or breathe out',
          'score': 1
        },
        {'text': 'B. Through direct touch', 'score': 0},
        {'text': 'C.By drinking unclean water', 'score': 0},
        {'text': 'D. All of the above', 'score': 0},
      ],
    },
    {
      'questionText':
          'How long does the novel coronavirus survive outside the body?',
      'answers': [
        {'text': 'A. A week in the air and on surfaces', 'score': 0},
        {'text': 'B. Several Hours to days', 'score': 1},
        {'text': 'C. Upto a Year', 'score': 0},
        {'text': 'D. Immediately dies', 'score': 0},
      ],
    },
    {
      'questionText': 'Where does Quarantine word come from?',
      'answers': [
        {'text': 'A. From Italian word quranta', 'score': 1},
        {'text': 'B. From Kratian word karantena', 'score': 0},
        {'text': 'C. From Spanish word cuaranta', 'score': 0},
        {'text': 'D. None of Them', 'score': 0},
      ],
    },
    {
      'questionText':
          'Who was the first member of a royal family in the world to die of Covid-19?',
      'answers': [
        {'text': 'A. Spanish Princess Maria Teressa', 'score': 1},
        {'text': 'B. Frederik, Crown Prince Denmark', 'score': 0},
        {'text': 'C. Haitham bin Tariq Al Said, Sultan of Oman', 'score': 0},
        {'text': 'D. None of them', 'score': 0},
      ],
    },
    {
      'questionText': 'Can I use antibiotics to fight Covid-19?',
      'answers': [
        {
          'text':
              'A. Yes, antibiotics strengthen the body’s immune system and can work against Covid-19.',
          'score': 0
        },
        {
          'text':
              'B. Yes, antibiotics work on bacterial infections and can also cure Covid-19.',
          'score': 0
        },
        {
          'text':
              'C. No, antibiotics work only on bacterial infection and Covid-19 is a viral infection.',
          'score': 1
        },
        {
          'text':
              'D. No, antibiotics can’t be used because WHO has banned their use for Covid-19.',
          'score': 0
        },
      ],
    },
  ];
  var _questionIndex = 0;
  var _totalScore = 0;

  void _resetQuiz() {
    setState(() {
      _questionIndex = 0;
      _totalScore = 0;
    });
  }

  void _answerQuestion(int score) {
    _totalScore += score;

    setState(() {
      _questionIndex++;
    });
    print(_questionIndex);
    if (_questionIndex < _questions.length) {
      print('We have more Questions');
    } else {
      print('No more Questions');
    }
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Corona Virus Quiz'),
        ),
        body: _questionIndex < _questions.length
            ? Quiz(
                answerQuestion: _answerQuestion,
                questionIndex: _questionIndex,
                questions: _questions,
              )
            : Result(_totalScore, _resetQuiz),
      ),
    );
  }
}
