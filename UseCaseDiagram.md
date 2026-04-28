```mermaid
graph LR
    CustomerActor((고객))
    ManagerActor((관리자))

    subgraph 리조트_객실예약_시스템
        RegisterCustomer([고객등록])
        SearchCustomer([고객조회])
        AuthCustomer([고객인증])

        RegisterRoom([객실등록])
        SearchRoom([객실조회])
        SearchRoomPrice([객실가격조회])

        Reserve([예약])
        Cancel([취소])
        SearchReservation([예약조회])
        PrintTotalCost([총비용 출력])
    end

    CustomerActor --- Reserve
    CustomerActor --- Cancel
    CustomerActor --- SearchReservation

    ManagerActor --- RegisterCustomer
    ManagerActor --- SearchCustomer
    ManagerActor --- RegisterRoom
    ManagerActor --- SearchRoom
    ManagerActor --- SearchRoomPrice

    Reserve -. "<<include>>" .-> AuthCustomer
    Reserve -. "<<include>>" .-> SearchRoom
    Reserve -. "<<include>>" .-> SearchRoomPrice
    Reserve -. "<<include>>" .-> PrintTotalCost

    Cancel -. "<<include>>" .-> SearchReservation
    Cancel -. "<<include>>" .-> SearchCustomer

    SearchRoomPrice -. "<<include>>" .-> SearchRoom