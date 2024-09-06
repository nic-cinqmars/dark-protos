find_package(Protobuf REQUIRED CONFIG)

if (${Protobuf_FOUND})
    message(STATUS "Found Protobuf package with version : ${Protobuf_VERSION}")
endif()

set(PROTO_FILES
    Account.proto
    Agent.proto
    CharacterClass.proto
    _Character.proto
    _Chat.proto
    Common.proto
    Customize.proto
    DediServer.proto
    _Defins.proto
    Friend.proto
    GatheringHall.proto
    Gm.proto
    InGame.proto
    Inventory.proto
    IronMace.proto
    _Item.proto
    Karma.proto
    Lobby.proto
    MarketPlace.proto
    Merchant.proto
    Operate.proto
    _PacketCommand.proto
    Party.proto
    Ranking.proto
    Religion.proto
    _Reward.proto
    Shop.proto
    Trade.proto
)

add_library(protos ${PROTO_FILES})
target_include_directories(protos INTERFACE ${CMAKE_CURRENT_BINARY_DIR})

target_link_libraries(protos
    PUBLIC
        protobuf::libprotobuf
)

protobuf_generate(TARGET protos LANGUAGE cpp)