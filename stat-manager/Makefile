# DO-NOT-REMOVE begin-copyright-block 
#
# Redistributions of any form whatsoever must retain and/or include the
# following acknowledgment, notices and disclaimer:
#
# This product includes software developed by Carnegie Mellon University.
#
# Copyright 2012 by Mohammad Alisafaee, Eric Chung, Michael Ferdman, Brian 
# Gold, Jangwoo Kim, Pejman Lotfi-Kamran, Onur Kocberber, Djordje Jevdjic, 
# Jared Smolens, Stephen Somogyi, Evangelos Vlachos, Stavros Volos, Jason 
# Zebchuk, Babak Falsafi, Nikos Hardavellas and Tom Wenisch for the SimFlex 
# Project, Computer Architecture Lab at Carnegie Mellon, Carnegie Mellon University.
#
# For more information, see the SimFlex project website at:
#   http://www.ece.cmu.edu/~simflex
#
# You may not use the name "Carnegie Mellon University" or derivations
# thereof to endorse or promote products derived from this software.
#
# If you modify the software you must place a notice on or within any
# modified version provided or made available to any third party stating
# that you have modified the software.  The notice shall include at least
# your name, address, phone number, email address and the date and purpose
# of the modification.
#
# THE SOFTWARE IS PROVIDED "AS-IS" WITHOUT ANY WARRANTY OF ANY KIND, EITHER
# EXPRESS, IMPLIED OR STATUTORY, INCLUDING BUT NOT LIMITED TO ANY WARRANTY
# THAT THE SOFTWARE WILL CONFORM TO SPECIFICATIONS OR BE ERROR-FREE AND ANY
# IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE,
# TITLE, OR NON-INFRINGEMENT.  IN NO EVENT SHALL CARNEGIE MELLON UNIVERSITY
# BE LIABLE FOR ANY DAMAGES, INCLUDING BUT NOT LIMITED TO DIRECT, INDIRECT,
# SPECIAL OR CONSEQUENTIAL DAMAGES, ARISING OUT OF, RESULTING FROM, OR IN
# ANY WAY CONNECTED WITH THIS SOFTWARE (WHETHER OR NOT BASED UPON WARRANTY,
# CONTRACT, TORT OR OTHERWISE).
#
# DO-NOT-REMOVE end-copyright-block   
# Get variables from Makefile.defs

include ../makefile.defs


.DEFAULT: all

.SUFFIXES: .stats_o
.SUFFIXES: .cpp

SOURCES = ../core/stats/stats.cpp ../core/stats/measurement.cpp ../core/stats/stats_calc.cpp $(wildcard ../core/debug/*.cpp)

%.stats_o: %.cpp
	$(GCC) $(GCC_OPTFLAGS) $(GCC_LANGFLAGS) -isystem $(BOOST_INCLUDE) -isystem $(SIMICS_INCLUDE) -DSELECTED_DEBUG=dev -DTARGET_PLATFORM=v9 -I.. -c $^ -o $@

all: stat-manager stat-collapse stat-sample

stat-manager: $(subst .cpp,.stats_o,$(SOURCES) stat-manager.cpp )
	echo $^
	$(GCC) $(GCC_OPTFLAGS) $(INCLUDES) -DSELECTED_DEBUG=dev -DTARGET_PLATFORM=v9 -I.. $^ -L../core $(BOOST_LIBRARIES) -pthread -static -o $@

stat-collapse: $(subst .cpp,.stats_o,$(SOURCES) stat-collapse.cpp )
	echo $^
	$(GCC) $(GCC_OPTFLAGS) $(INCLUDES) -DSELECTED_DEBUG=dev -DTARGET_PLATFORM=v9 -I.. $^ -L../core $(BOOST_LIBRARIES) -pthread -static -o $@

stat-sample: $(subst .cpp,.stats_o,$(SOURCES) stat-sample.cpp )
	echo $^
	$(GCC) $(GCC_OPTFLAGS) $(INCLUDES) -DSELECTED_DEBUG=dev -DTARGET_PLATFORM=v9 -I.. $^ -L../core $(BOOST_LIBRARIES) -pthread -static -o $@


clean:
	rm -f *.stats_o stat-manager stat-sample stat-collapse $(subst .cpp,.stats_o,$(SOURCES) )
