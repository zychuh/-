//直接把源代码丢这里得了

#include <iostream>

#include <cstdlib>

#include <ctime>

#include <fstream>

#include <vector>

using namespace std;

 

char getDigit()

{

    return static_cast<char>('0' + rand()%('9'-'0'+1));

}

char getLower()

{

    return static_cast<char>('a' + rand()%('z'-'a'+1));

}

char getUpper()

{

    return static_cast<char>('A' + rand()%('Z'-'A'+1));

}

char getSpecial()

{

    return static_cast<char>('(' + rand()%('/'-'('+1));

}

int main()

{

    ofstream output;

    output.open("密码在此.txt");

    srand(time(0));

    char ch;    //保存随机生成的字符

    int num;    //决定随机生成字符的类型

    int npwd;   //输出密码的个数

    char type;  //决定密码是否包含特殊字符

    vector<char> str; //保存随机生成的字符串

    int count = 0; //判断某个密码中是否含有特殊字符

    cout << "密码是否需要带有特殊字符" << endl;

    cout << "(输Y即要，输N即不要，然后回车)"<<endl;

    cin >> type;

    if(type != 'Y' && type != 'N')

    {

        cout << "错误!" << endl;

        return 0;

    }

    cout << "输入一次性需要的密码数量并回车"<<endl;

    cin >> npwd;

    for(int j=0; j<npwd; j++)

    {

        for(int i=0; i<10; i++) //默认生成十位字符串密码

            {

                if(type == 'Y')

                    num = rand()%4;

                else

                    num = rand()%3;

                if(num == 0)

                    ch = getDigit();

                else if(num == 1)

                    ch = getLower();

                else if(num == 2)

                    ch = getUpper();

                else

                    {

                        ch = getSpecial();

                        count++;

                    }

                    str.push_back(ch);

            }

    while(type=='Y' && count==0)

    {

        str.clear();

        for(int i=0; i<10; i++) //默认生成十位字符串密码

            {

                if(type == 'Y')

                    num = rand()%4;

                else

                    num = rand()%3;

                if(num == 0)

                    ch = getDigit();

                else if(num == 1)

                    ch = getLower();

                else if(num == 2)

                    ch = getUpper();

                else

                    {

                        ch = getSpecial();

                        count++;

                    }

                    str.push_back(ch);

            }

    }

    count = 0;

    vector<char>::iterator p1;

        for(p1=str.begin(); p1!=str.end();p1++)

        {

            output << *p1;

        }

    output << endl;

    str.clear();

    }

    cout << "Done" << endl;

 

    return 0;

}

