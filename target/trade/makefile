.SUFFIXES:  .c .cpp .o .obj .a .lib

CPP=g++ -fpic
LINK=g++
LIB32=ar -ru
PREP=g++ -E -P
PUMP=pump
COPY=cp
DEL=rm
MAKE=make
ECHO=echo

.cpp.o:
	$(CPP) $(CPPFLAGS) $(INCLUDEDIR) -c $< -o $@ 2>> output



ISLIB=N
DEFINES=-DHP_UX -DGCC
target=././trade

DEBUG_DEFINE=-DDEBUG -DDEBUG_LOG

APPEND_CPPFLAGS=-O3 -pthread -m64

PROFILE_CPPFLAGS=

WARNING_CPPFLAGS=-Wall -Wno-sign-compare

CPPFLAGS= -fpermissive -g -ggdb3             $(APPEND_CPPFLAGS) $(PROFILE_CPPFLAGS) $(WARNING_CPPFLAGS) $(DEBUG_DEFINE) $(DEFINES)

LIBS= -lpthread             

DEBUG_LDFLAGS=-O3 -m64

MAP_LDFLAGS=

PROFILE_LDFLAGS=

WARNING_LDFLAGS=-Wall -Wno-sign-compare

LDFLAGS=              $(MAP_LDFLAGS) $(DEBUG_LDFLAGS) $(PROFILE_LDFLAGS) $(WARNING_LDFLAGS)

LIBARFLAGS=             -static $(MAP_LDFLAGS) $(DEBUG_LDFLAGS) $(PROFILE_LDFLAGS)

DLLARFLAGS=             -shared  -Wl,-Bsymbolic $(MAP_LDFLAGS) $(DEBUG_LDFLAGS) $(PROFILE_LDFLAGS)


all: code

code: clearoutput $(target)

clearoutput:
	@$(ECHO) Compiling... > output

utils_obj= ../../src/base/utils/Lib.o  ../../src/base/utils/Logger.o 
utils_include= ../../src/base/utils/Lib.h  ../../src/base/utils/Logger.h  ../../src/base/utils/global.h 
utils_includedir=-I../../src/base/utils/.
ini_obj= ../../src/base/ini/Inifile.o 
ini_include=
ini_includedir=-I../../src/base/ini/.
json_obj= ../../src/base/json/json_reader.o  ../../src/base/json/json_value.o  ../../src/base/json/json_writer.o 
json_include= ../../src/base/json/json_batchallocator.h  ../../src/base/json/json/autolink.h  ../../src/base/json/json/config.h  ../../src/base/json/json/features.h  ../../src/base/json/json/forwards.h  ../../src/base/json/json/json.h  ../../src/base/json/json/reader.h  ../../src/base/json/json/value.h  ../../src/base/json/json/writer.h 
json_includedir=-I../../src/base/json/.
redis_obj= ../../src/base/redis/Redis.o 
redis_lib=-L../../src/base/redis/ -lhiredis -lxredis
redis_include= ../../src/base/redis/Redis.h 
redis_includedir=-I../../src/base/redis/.
printfc_obj= ../../src/base/printfc/printfc.o 
printfc_include=
printfc_includedir=-I../../src/base/printfc/.
thread_obj= ../../src/base/thread/Thread.o 
thread_include=
thread_includedir=-I../../src/base/thread/.
baseexchapi_obj=
baseexchapi_include= ../../src/business/engine/UserApiStruct.h  ../../src/business/engine/UserApiDataType.h  ../../src/business/engine/BaseExchApi.h 
baseexchapi_includedir=-I../../src/business/engine/.
Thostlink_obj= ../../src/business/ctp/ThostMdLink.o  ../../src/business/ctp/ThostTradeLink.o 
Thostlink_lib=-L../../src/business/ctp/ -lthostmduserapi -lthosttraderapi
Thostlink_include= ../../src/business/ctp/ThostFtdcMdApi.h  ../../src/business/ctp/ThostFtdcTraderApi.h  ../../src/business/ctp/ThostFtdcUserApiDataType.h  ../../src/business/ctp/ThostFtdcUserApiStruct.h  ../../src/business/ctp/ThostMdLink.h  ../../src/business/ctp/ThostTradeLink.h 
Thostlink_includedir=-I../../src/business/ctp/.
linkmanager_obj= ../../src/business/linkmanager/GateLinkManager.o 
linkmanager_include= ../../src/business/linkmanager/GateLinkManager.h 
linkmanager_includedir=-I../../src/business/linkmanager/.
trade_obj= ../../src/business/trade/trade.o 
trade_lib=-L../../src/business/trade/
trade_include=
trade_includedir=-I../../src/business/trade/.

all_objs= $(utils_obj)  $(ini_obj)  $(json_obj)  $(redis_obj)  $(printfc_obj)  $(thread_obj)  $(baseexchapi_obj)  $(Thostlink_obj)  $(linkmanager_obj)  $(trade_obj) 
all_libs= $(utils_lib)  $(ini_lib)  $(json_lib)  $(redis_lib)  $(printfc_lib)  $(thread_lib)  $(baseexchapi_lib)  $(Thostlink_lib)  $(linkmanager_lib)  $(trade_lib) 
INCLUDEDIR= $(utils_includedir)  $(ini_includedir)  $(json_includedir)  $(redis_includedir)  $(printfc_includedir)  $(thread_includedir)  $(baseexchapi_includedir)  $(Thostlink_includedir)  $(linkmanager_includedir)  $(trade_includedir) 

../../src/base/utils/Lib.o: ../../src/base/utils/Lib.cpp $(utils_include)   $(ini_include) $(printfc_include)
../../src/base/utils/Logger.o: ../../src/base/utils/Logger.cpp $(utils_include)   $(ini_include) $(printfc_include)
../../src/base/ini/Inifile.o: ../../src/base/ini/Inifile.cpp $(ini_include)  
../../src/base/json/json_reader.o: ../../src/base/json/json_reader.cpp $(json_include)  
../../src/base/json/json_value.o: ../../src/base/json/json_value.cpp $(json_include)  
../../src/base/json/json_writer.o: ../../src/base/json/json_writer.cpp $(json_include)  
../../src/base/redis/Redis.o: ../../src/base/redis/Redis.cpp $(redis_include)   $(ini_include) $(utils_include)
../../src/base/printfc/printfc.o: ../../src/base/printfc/printfc.cpp $(printfc_include)  
../../src/base/thread/Thread.o: ../../src/base/thread/Thread.cpp $(thread_include)  
../../src/business/ctp/ThostMdLink.o: ../../src/business/ctp/ThostMdLink.cpp $(Thostlink_include)   $(redis_include) $(baseexchapi_include)
../../src/business/ctp/ThostTradeLink.o: ../../src/business/ctp/ThostTradeLink.cpp $(Thostlink_include)   $(redis_include) $(baseexchapi_include)
../../src/business/linkmanager/GateLinkManager.o: ../../src/business/linkmanager/GateLinkManager.cpp $(linkmanager_include)  
../../src/business/trade/trade.o: ../../src/business/trade/trade.cpp $(trade_include)   $(ini_include) $(utils_include) $(json_include) $(baseexchapi_include) $(Thostlink_include) $(redis_include)

copytargetall= 
pumptargetall= 

$(target): $(all_objs)
	$(LINK) $(LDFLAGS) -o $@ $(all_objs) $(all_libs) $(LIBS) >> output


clean:
	-$(DEL) $(utils_obj)
	-$(DEL) $(ini_obj)
	-$(DEL) $(json_obj)
	-$(DEL) $(redis_obj)
	-$(DEL) $(printfc_obj)
	-$(DEL) $(thread_obj)
	-$(DEL) $(baseexchapi_obj)
	-$(DEL) $(Thostlink_obj)
	-$(DEL) $(linkmanager_obj)
	-$(DEL) $(trade_obj)
	-$(DEL) $(copytargetall)
	-$(DEL) $(pumptargetall)
	-$(DEL) $(target)

pump: $(pumptargetall)

