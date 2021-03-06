---
layout: page
title: "Q168936: FIX: Virtual Base Class Destructor Called More than Once"
permalink: /kb/168/Q168936/
---

## Q168936: FIX: Virtual Base Class Destructor Called More than Once

{% raw %}

	Article: Q168936
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1,4.2,5.0
	Operating System(s): 
	Keyword(s): kbtool kbCompiler kbCPPonly kbVC kbVC400bug kbVC410bug kbVC420bug kbVC500bug kbVC600fix
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If an exception is thrown from the constructor of a class that is derived from a
	virtual base class, the destructor for the virtual base class is called more
	than once. This doesn't happen if the exception is thrown from any other member
	function.
	
	RESOLUTION
	==========
	
	There is no workaround. Avoid throwing exceptions from the constructor.
	
	For additional information about the two-phased construction, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q132893 PRB: Exceptions Thrown During Construction Can Orphan Memory
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected in Visual C++ version 6.0
	for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	     //compiler options needed  /GX
	
	      #include <iostream.h>
	      class A
	      {
	        public:
	              A() { cout << "In A-ctor" << endl;}
	              ~A(){ cout << "In A-dtor" << endl;}
	      };
	
	      class B1 : public  virtual   A
	      {
	        public:
	                B1() { cout << "In B1-ctor" << endl;}
	              ~B1(){ cout << "In B1-dtor" << endl;}
	      };
	
	      class B2 : public  virtual  A
	      {
	        public:
	                B2() { cout << "In B2-ctor" << endl;}
	              ~B2(){ cout << "In B2-dtor" << endl;}
	      };
	
	      class C : public B1 ,public B2
	      {
	        public:
	            C(){
	           cout << "In C-ctor...throw Exception" << endl;
	           throw int(1); //incorrect destructor calls...
	               }
	
	            ~C(){ cout << "In C-dtor" << endl;}
	      };
	
	      void main()
	      {
	        try
	         {
	           C c;
	
	         }
	        catch (int ex)
	         {
	           cout << "Caught Exception #" << ex << endl;
	           }
	      }
	
	The program output is:
	
	  In A-ctor
	  In B1-ctor
	  In B2-ctor
	  In C-ctor...throw Exception
	  In B2-dtor
	  In A-dtor
	  In B1-dtor
	  In A-dtor
	  In A-dtor
	  Caught Exception #1
	
	The expected output is:
	
	  In A-ctor
	  In B1-ctor
	  In B2-ctor
	  In C-ctor...throw Exception
	  In B2-dtor
	  In B1-dtor
	  In A-dtor
	  Caught Exception #1
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool kbCompiler kbCPPonly kbVC kbVC400bug kbVC410bug kbVC420bug kbVC500bug kbVC600fix 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : winnt:4.0,4.1,4.2,5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
