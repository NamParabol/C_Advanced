# Compiler and flags
CC = gcc
LIBS = -pthread
CFLAGS = -Wall -g\
-I.\BSW\ECU_Abstraction\IoHwAb\
-I.\BSW\MCAL\
-I.\BSW\Services\
-I.\RTE\
-I.\SWC
# Object directory
OBJDIR = bin
# Executable
TARGET = $(OBJDIR)/ecu

SRC = ./BSW/ECU_Abstraction/IoHwAb/IohwAb_CurrentSensor.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_LoadSensor.c \
./BSW/ECU_Abstraction/IoHwAb/IohwAb_MotorControl.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_MotorDriver.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_MotorSpeedSensor.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_SpeedSensor.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_ThrottleSensor.c \
./BSW/ECU_Abstraction/IoHwAb/IoHwAb_TorqueSensor.c \
./BSW/MCAL/Adc.c \
./BSW/MCAL/Can.c \
./BSW/MCAL/Dio.c \
./BSW/MCAL/Pwm.c \
./BSW/Services/Dcm.c \
./BSW/Services/Dem.c \
./BSW/Services/Mem.c \
./BSW/Services/Os.c \
./BSW/Services/Pdu_Router.c \
./Main.c \
./RTE/Rte_SpeedControl.c \
./RTE/Rte_TorqueControl.c \
./SWC/Speed_Control.c \
./SWC/Torque_Control.c 

# Object files
OBJ = $(SRC:%.c=$(OBJDIR)/%.o)

# Build executable
$(TARGET): $(OBJ)
	@echo "Linking all objects to create $(TARGET)..."
	$(CC) $(CFLAGS) $(LIBS) -o $(TARGET) $(OBJ)
	@echo "Build successful!"

# Compile object files
$(OBJDIR)/%.o: %.c
	@if not exist $(OBJDIR) mkdir $(OBJDIR)
	@if not exist $(dir $@) mkdir $(dir $@)
	$(CC) $(CFLAGS) -c $< -o $@
	@echo "Compiled: $<"

# Clean up
.PHONY: clean
clean:
	@echo "Cleaning up..."
	@if exist $(OBJDIR) rmdir /s /q $(OBJDIR)
	@echo "Clean done!"

# Run program
.PHONY: run
run: $(TARGET)
	@echo "Running program..."
	$(TARGET)
