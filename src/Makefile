CC = gcc
CXX = g++
CFLAGS = -O2 -ffast-math -fomit-frame-pointer -Irubber1.0 -FOpenGL -FGLUT -FCarbon
CXXFLAGS = -O2 -ffast-math -fomit-frame-pointer -Irubber1.0 -std=c++0x -FOpenGL -FGLUT -FCarbon
LIBS = ./libbass.dylib -framework GLUT -framework OpenGL -lm -lc -framework Cocoa -rpath "@executable_path/../Frameworks"
APP_DIR = OneFinger.app

OBJ = test3d.o Kewlmation.o \
      rubber1.0/Rubber.o rubber1.0/Shader.o rubber1.0/Texture.o \
      rubber1.0/Model.o rubber1.0/Camera.o rubber1.0/Datafile.o \
      rubber1.0/Fbo.o rubber1.0/BassRocket.o \
      rocket/sync/data.o rocket/sync/device.o rocket/sync/track.o

onefinger: $(OBJ)
	$(CXX) -o $@ $(OBJ) $(LIBS)
	strip $@

create_app:
	mkdir -p $(APP_DIR)/Contents/{MacOS,Resources,Frameworks}
	cp Info.plist $(APP_DIR)/Contents/Info.plist
	cp Kewlers.icns $(APP_DIR)/Contents/Resources/Kewlers.icns
	cp onefinger $(APP_DIR)/Contents/MacOS
	cp libbass.dylib $(APP_DIR)/Contents/Frameworks
	cp -r data $(APP_DIR)/Contents/Resources
	install_name_tool -id "@executable_path/../Frameworks/libbass.dylib" "OneFinger.app/Contents/Frameworks/libbass.dylib"
	codesign --force --deep --sign - "OneFinger.app"

clean:
	-rm $(OBJ) onefinger
