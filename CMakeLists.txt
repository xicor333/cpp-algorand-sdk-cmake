cmake_minimum_required(VERSION 3.12)
project(cpp-algorand-sdk)

set(CMAKE_CXX_STANDARD 14)

find_library(SODIUM_LIB libsodium REQUIRED)
find_library(CRYPTO_LIB libcrypto REQUIRED)
find_library(CURL_LIB libcurl REQUIRED)

add_library(cpp-algorand-sdk)

target_sources(cpp-algorand-sdk
	PUBLIC
		include/algorand.h
		include/base.h
		include/mnemonic.h
	PRIVATE
		src/base.cpp
		src/clients.cpp
		src/mnemonic.cpp
)
target_include_directories(cpp-algorand-sdk
	PUBLIC
	include
)

target_link_libraries(cpp-algorand-sdk
	PRIVATE
	${SODIUM_LIB}
	${CRYPTO_LIB}
	${CURL_LIB}
)