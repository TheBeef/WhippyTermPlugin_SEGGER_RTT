CC = g++
# add -g for debugging info
CC_FLAGS = -g -Wall -fmax-errors=1 -Wfatal-errors -Wno-memset-transposed-args -fPIC -D __STDC_FORMAT_MACROS=1 -D __USE_MINGW_ANSI_STDIO
LNK_FLAGS = -shared

# Final binary
BIN = SEGGER_RTT.dll

# Put all auto generated stuff to this build dir.
BUILD_DIR = build

SOURCE_DIR = ..

SRC_DIR = src
LIBS_DIR = ..

# List of all .c source files.
SOURCE = $(SRC_DIR)\SEGGER_RTT_Main.cpp \
	$(SRC_DIR)\SEGGER_RTT_AuxWidgets.cpp \
	$(SRC_DIR)\SEGGER_RTT_Common.cpp \
	$(SRC_DIR)\OS\Win\SEGGER_RTT_OS_JLinkARM.cpp \

INCLUDES = ..\src \

# All .o files go to build dir.
OBJ = $(SOURCE:%.c=$(BUILD_DIR)\\%.o)
OBJ = $(SOURCE:%.cpp=$(BUILD_DIR)\\%.o)
# Gcc/Clang will create these .d files containing dependencies.
DEP = $(OBJ:%.o=%.d)
# Include paths with a -I in front of them
CC_INCLUDE = $(INCLUDES:%= -I %)

# Default target named after the binary.
$(BIN) : $(BUILD_DIR)\\$(BIN)

# Actual target of the binary - depends on all .o files.
$(BUILD_DIR)\\$(BIN): $(OBJ)
	echo Linking...
	-mkdir $(@D) 2>NUL
	$(CC) $(CC_FLAGS) $(OBJ) $(LNK_FLAGS) -o $@
	-copy $(BUILD_DIR)\\$(BIN) $(BIN)

# Include all .d files
-include $(DEP)

# Build target for every single object file.
# The potential dependency on header files is covered
# by calling `-include $(DEP)`.
$(BUILD_DIR)\\%.o : $(SOURCE_DIR)\%.cpp
	echo Compiling $(notdir $<)
	-mkdir $(@D)
	$(CC) $(CC_FLAGS) $(CC_INCLUDE) -MMD -c $< -o $@

$(BUILD_DIR)\\%.o : $(SOURCE_DIR)\%.c
	echo Compiling $(notdir $<)
	-mkdir $(@D)
	$(CC) $(CC_FLAGS) $(CC_INCLUDE) -MMD -c $< -o $@

#.PHONY : clean
clean:
	-rd /s/q $(BUILD_DIR)
