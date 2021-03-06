INCLUDE_DIRECTORIES (
	${PROJECT_SOURCE_DIR}/opencog/atomspace
	${PROJECT_SOURCE_DIR}/opencog/query
	${PROJECT_SOURCE_DIR}/opencog/util	
	${PROJECT_SOURCE_DIR}/opencog/reasoning/RuleEngine/rule-engine-src
	${PROJECT_SOURCE_DIR}/opencog/reasoning/RuleEngine/rule-engine-src/pln
)

LINK_DIRECTORIES(
	${PROJECT_BINARY_DIR}/opencog/atomspace
	${PROJECT_BINARY_DIR}/opencog/query
	${PROJECT_BINARY_DIR}/opencog/util
	${PROJECT_BINARY_DIR}/opencog/reasoning/RuleEngine/rule-engine-src
)

LINK_LIBRARIES(
	atomspace
	query
	server
	ruleengine
)

IF (HAVE_GUILE)
	ADD_CXXTEST(RuleUTest)
	#ADD_CXXTEST(ForwardChainerUTest)
	#ADD_CXXTEST(BackwardChainerUTest)
	#ADD_CXXTEST(PLNCommonsUTest)
	ADD_CXXTEST(JsonicControlPolicyParamLoaderUTest)
	ADD_CXXTEST(DefaultForwardChainerCBUTest)
ENDIF (HAVE_GUILE)

CONFIGURE_FILE(${CMAKE_SOURCE_DIR}/tests/reasoning/RuleEngine/simple-assertions.scm
    ${PROJECT_BINARY_DIR}/tests/reasoning/RuleEngine/simple-assertions.scm)
 
CONFIGURE_FILE(${CMAKE_SOURCE_DIR}/tests/reasoning/RuleEngine/bc-test/bc-example.scm
    ${PROJECT_BINARY_DIR}/tests/reasoning/RuleEngine/bc-test/bc-example.scm)   
    
CONFIGURE_FILE(${CMAKE_SOURCE_DIR}/tests/reasoning/RuleEngine/test_cpolicy.json
    ${PROJECT_BINARY_DIR}/tests/reasoning/RuleEngine/rules/pln/test_cpolicy.json)     
    