cl-opencalais : A Common Lisp Wrapper for the OpenCalais API
============================================================

Introduction
------------

The [Thomson Reuters Calais Web Service](http://www.opencalais.com/)
takes unstructured text and returns Resource Description Framework
(RDF) formatted results identifying entities, facts and events within
the content.

cl-opencalais defines a very simple wrapper based on 
[Drakma](http://weitz.de/drakma/)
that makes OpenCalais easy to call from Common Lisp.

Tested with SBCL on Linux.

The code comes with a 
[BSD-style license](http://www.opensource.org/licenses/bsd-license.php) 
so you can basically do whatever you want with it.

Example
-------

	CL-USER> (asdf:oos 'asdf:load-op :cl-opencalais)

	...
	
	NIL
	CL-USER> (defparameter *key* "YOURCALAISKEY")
	*KEY*
	CL-USER> (cl-opencalais:enlighten *key* "The Queen lives in London, England" "")

	...
	
	"OK"
	CL-USER> 

By default, the result is a lump of RDF XML which can easily be parsed
with [cxml](http://common-lisp.net/project/cxml/)

	CL-USER> (cxml:parse (cl-opencalais:enlighten *key* 
	"Bill Gates lives in Redmond" "") (cxml-dom:make-dom-builder))
	
	#<RUNE-DOM::DOCUMENT {1003878651}>
	CL-USER> 

[Rob Blackwell](mailto://rob.blackwell@aws.net),
September 2009.
