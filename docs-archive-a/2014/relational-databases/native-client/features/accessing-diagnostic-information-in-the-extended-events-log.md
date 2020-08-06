---
title: 拡張イベント ログの診断情報へのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 5148683d464f06e8a4f52cc924baaacac9102b12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714293"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a><span data-ttu-id="22b19-102">拡張イベント ログの診断情報へのアクセス</span><span class="sxs-lookup"><span data-stu-id="22b19-102">Accessing Diagnostic Information in the Extended Events Log</span></span>
  <span data-ttu-id="22b19-103">以降で [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client とデータアクセスのトレース ([データアクセスのトレース](https://go.microsoft.com/fwlink/?LinkId=125805)) が更新され、接続リングバッファーおよび拡張イベントログからのアプリケーションのパフォーマンス情報からの接続エラーに関する診断情報を簡単に取得できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="22b19-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data access tracing ([Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805)) have been updated to make it easier to get diagnostic information about connection failures from the connectivity ring buffer and application performance information from the extended events log.</span></span>  
  
 <span data-ttu-id="22b19-104">拡張イベント ログを表示する方法については、「[イベント セッション データの表示](../../../database-engine/view-event-session-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22b19-104">For information about reading the extended events log, see [View Event Session Data](../../../database-engine/view-event-session-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="22b19-105">この機能は、トラブルシューティングおよび診断用であるため、監査やセキュリティの用途には適さない場合があります。</span><span class="sxs-lookup"><span data-stu-id="22b19-105">This feature is intended only for troubleshooting and diagnostic purposes and may not be suitable for auditing or security purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22b19-106">解説</span><span class="sxs-lookup"><span data-stu-id="22b19-106">Remarks</span></span>  
 <span data-ttu-id="22b19-107">接続操作では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はクライアント接続 ID を送信します。</span><span class="sxs-lookup"><span data-stu-id="22b19-107">For connection operations, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will send a client connection ID.</span></span> <span data-ttu-id="22b19-108">接続に失敗した場合は、接続リング バッファー ([接続リング バッファーによる SQL Server 2008 での接続トラブルシューティング](https://go.microsoft.com/fwlink/?LinkId=207752)に関する記事を参照) にアクセスし、`ClientConnectionID` フィールドを見つけて、接続エラーに関する診断情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="22b19-108">If the connection fails, you can access the connectivity ring buffer ([Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer](https://go.microsoft.com/fwlink/?LinkId=207752)) and find the `ClientConnectionID` field and get diagnostic information about the connection failure.</span></span> <span data-ttu-id="22b19-109">クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます。</span><span class="sxs-lookup"><span data-stu-id="22b19-109">Client connection IDs are logged in the ring buffer only if an error occurs.</span></span> <span data-ttu-id="22b19-110">(ログイン前のパケットを送信する前に接続に失敗した場合、クライアント接続 ID は生成されません。)クライアント接続 ID は 16 バイトの GUID です。</span><span class="sxs-lookup"><span data-stu-id="22b19-110">(If a connection fails before sending the prelogin packet, a client connection ID will not be generated.) The client connection ID is a 16-byte GUID.</span></span> <span data-ttu-id="22b19-111">拡張イベント `client_connection_id` セッションのイベントにアクションが追加されている場合は、拡張イベントの出力ターゲットでクライアント接続 ID を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="22b19-111">You can also find the client connection ID in the extended events output target, if the `client_connection_id` action is added to events in an extended events session.</span></span> <span data-ttu-id="22b19-112">詳しい診断サポートが必要な場合は、データ アクセスのトレースを有効にして、接続コマンドを再実行し、失敗した操作のデータ アクセスのトレースで `ClientConnectionID` フィールドを調べます。</span><span class="sxs-lookup"><span data-stu-id="22b19-112">You can enable data access tracing and rerun the connection command and observe the `ClientConnectionID` field in the data access trace for a failed operation, if you need further diagnostic assistance.</span></span>  
  
 <span data-ttu-id="22b19-113">Native Client で ODBC を使用していて、接続に成功した場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `SQL_COPT_SS_CLIENT_CONNECTION_ID` [Sqlgetconnectattr](../../native-client-odbc-api/sqlgetconnectattr.md)属性を使用して、クライアント接続 ID を取得できます。</span><span class="sxs-lookup"><span data-stu-id="22b19-113">If you are using ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and a connection succeeds, you can get the client connection ID by using the `SQL_COPT_SS_CLIENT_CONNECTION_ID` attribute with [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="22b19-114">Native Client は、スレッド固有のアクティビティ ID も送信します。</span><span class="sxs-lookup"><span data-stu-id="22b19-114">Native Client also sends a thread-specific activity ID.</span></span> <span data-ttu-id="22b19-115">アクティビティ ID は、TRACK_CAUSAILITY オプションを有効にしてセッションを開始した場合、拡張イベント セッションでキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="22b19-115">The activity ID is captured in the extended events sessions if the sessions are started with the TRACK_CAUSAILITY option enabled.</span></span> <span data-ttu-id="22b19-116">アクティブな接続のパフォーマンスの問題については、クライアントのデータ アクセスのトレース (`ActivityID` フィールド) からアクティビティ ID を取得した後、その拡張イベントの出力のアクティビティ ID を検索できます。</span><span class="sxs-lookup"><span data-stu-id="22b19-116">For performance issues with an active connection, you can get the activity ID from the client's data access trace (`ActivityID` field) and then locate the activity ID in the extended events output.</span></span> <span data-ttu-id="22b19-117">拡張イベントのアクティビティ ID は、16 バイトの GUID (クライアント接続 ID の GUID とは異なります) に 4 バイトのシーケンス番号が付加されたものです。</span><span class="sxs-lookup"><span data-stu-id="22b19-117">The activity ID in the extended events is a 16-byte GUID (not the same as the GUID for the client connection ID) appended with a four-byte sequence number.</span></span> <span data-ttu-id="22b19-118">シーケンス番号は、スレッド内で要求の順序を表し、スレッドのバッチと RPC ステートメントの相対的順序を示します。</span><span class="sxs-lookup"><span data-stu-id="22b19-118">The sequence number represents the order of a request within a thread and indicates the relative ordering of batch and RPC statements for the thread.</span></span> <span data-ttu-id="22b19-119">`ActivityID` は必要に応じて、データ アクセスのトレースが有効であり、データ アクセス トレース構成ワードの 18 番目のビットがオンである場合に、SQL バッチ ステートメントと RPC 要求に送信されます。</span><span class="sxs-lookup"><span data-stu-id="22b19-119">The `ActivityID` is optionally sent for SQL batch statements and RPC requests when data access tracing is enabled on and the 18th bit in the data access tracing configuration word is turned ON.</span></span>  
  
 <span data-ttu-id="22b19-120">次のサンプルでは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して拡張イベント セッションを開始します。このセッションは、リング バッファーに保存され、RPC およびバッチ操作でクライアントから送信されたアクティビティ ID を記録します。</span><span class="sxs-lookup"><span data-stu-id="22b19-120">The following is a sample that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to start an extended events session that will be stored in a ring buffer and will record the activity ID sent from a client on RPC and batch operations.</span></span>  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a><span data-ttu-id="22b19-121">制御ファイル</span><span class="sxs-lookup"><span data-stu-id="22b19-121">Control File</span></span>  
 <span data-ttu-id="22b19-122">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の SQL Server Native Client 制御ファイル (ctrl.guid.snac11) の内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="22b19-122">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client control file (ctrl.guid.snac11) is:</span></span>  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a><span data-ttu-id="22b19-123">MOF ファイル</span><span class="sxs-lookup"><span data-stu-id="22b19-123">MOF File</span></span>  
 <span data-ttu-id="22b19-124">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の SQL Server Native Client MOF ファイルの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="22b19-124">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client mof file is:</span></span>  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="22b19-125">参照</span><span class="sxs-lookup"><span data-stu-id="22b19-125">See Also</span></span>  
 [<span data-ttu-id="22b19-126">エラーとメッセージの処理</span><span class="sxs-lookup"><span data-stu-id="22b19-126">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
