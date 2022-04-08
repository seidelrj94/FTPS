file(GLOB client_files ftp_client*.cpp)
file(GLOB server_files ftp_server*.cpp)
            
target_sources(ftp_client PRIVATE ${client_files})
target_sources(ftp_server PRIVATE ${server_files})