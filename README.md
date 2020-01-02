Log version: CatLog_Sington 1.0.0.0
=======
[![Build Status](https://travis-ci.org/graycatya/Log.svg?branch=master)](https://travis-ci.org/graycatya/Log)



```
#include <iostream>
#include <functional>
#include "../CatLog/CatLog_Sington.h"

#define NUM 10000

using namespace CATLOG;

int main()
{
    CatLog::Instance();
    std::thread thread_test_0([]{
        for(int i = 0; i < NUM; i++)
        {
            CATLOG::__Write_Log("./test0",__DEBUG_LOG("log: " + std::to_string(i)));
        }
    });
    std::thread thread_test_1([]{
        for(int i = 0; i < NUM; i++)
        {
            CATLOG::__Write_Log("./test1",__INFO_LOG("log: " + std::to_string(i)));
        }
    });
    std::thread thread_test_2([]{
        for(int i = 0; i < NUM; i++)
        {
            CATLOG::__Write_Log("./test2",_DEBUG_LOG("log: " + std::to_string(i)));
        }
    });
    std::thread thread_test_3([]{
        for(int i = 0; i < NUM; i++)
        {
            CATLOG::__Write_Log(__WARN_LOG("log: " + std::to_string(i)));
        }
    });
    std::thread thread_test_4([]{
        for(int i = 0; i < NUM; i++)
        {
            CATLOG::__Write_Log("./test4", __ALARM_LOG("log: " + std::to_string(i)));
        }
    });
    for(int i = 0; i < NUM; i++)
    {
        CATLOG::__Write_Log(_INFO_LOG("log: " + std::to_string(i)));
    }
    thread_test_0.join();
    thread_test_1.join();
    thread_test_2.join();
    thread_test_3.join();
    thread_test_4.join();
    CatLog::Delete();
    return 0;
}
```
