first_rule: all

all: build install

export PYTHONPATH=$(CURDIR)/../../OBJ/lib

PACKAGE_NAME := PyQt4_gpl_x11-4.12.3
PACKAGE_DIR := PyQt4_gpl_x11-4.12.3

# Configuration
PACKAGE_CONF := \
	--confirm-license  \
	--enable=QtWebKit  \
	--enable=QtWebKitWidgets \
	--sip=$(CURDIR)/../../OBJ/bin/sip \
	--sipdir=$(CURDIR)/../../OBJ/bin/ \
	--destdir=$(CURDIR)/../../OBJ/lib \
	--bindir=$(CURDIR)/../../OBJ/bin \
	
test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_NAME).tar.gz -C $(CURDIR)/../../TARGET/; \
	fi

build_lib: test_directory
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ && python ./configure.py  $(PACKAGE_CONF); \

build: build_lib
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ all

pre_install_check:
	if [ ! -d $(CURDIR)/../../OBJ/lib ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/lib; \
	fi
	if [ ! -d $(CURDIR)/../../OBJ/bin ]; then \
	    mkdir -p $(CURDIR)/../../OBJ/bin; \
	fi

install: pre_install_check
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ install
	
config_rule:

clean_rule:

uninstall_rule:
