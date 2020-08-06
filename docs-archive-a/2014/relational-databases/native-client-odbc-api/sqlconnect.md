---
title: SQLConnect |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLConnect function
ms.assetid: 6da74e3a-4388-4907-81cb-987389bae467
author: rothja
ms.author: jroth
ms.openlocfilehash: 43b37ae16638e461e37edaead83cd9ceedc1c86d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640924"
---
# <a name="sqlconnect"></a><span data-ttu-id="1108f-102">SQLConnect</span><span class="sxs-lookup"><span data-stu-id="1108f-102">SQLConnect</span></span>
  <span data-ttu-id="1108f-103">接続が開いている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、SQL_COPT_SS_MUTUALLY_AUTHENTICATED および SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD が、接続を開くときに使用された認証方式に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1108f-103">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span> <span data-ttu-id="1108f-104">Spn の詳細については、「[クライアント接続 &#40;ODBC&#41;のサービスプリンシパル名 &#40;spn&#41; ](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1108f-104">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="sqlconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="1108f-105">SQLConnect の HADR サポート</span><span class="sxs-lookup"><span data-stu-id="1108f-105">SQLConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="1108f-106">**SQLConnect**を使用してクラスターに接続する方法の詳細については、 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 「[高可用性、ディザスターリカバリーのサポートの SQL Server Native Client](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1108f-106">For more information on using **SQLConnect** to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1108f-107">参照</span><span class="sxs-lookup"><span data-stu-id="1108f-107">See Also</span></span>  
 <span data-ttu-id="1108f-108">[SQLConnect 関数](https://go.microsoft.com/fwlink/?LinkId=101541) </span><span class="sxs-lookup"><span data-stu-id="1108f-108">[SQLConnect Function](https://go.microsoft.com/fwlink/?LinkId=101541) </span></span>  
 [<span data-ttu-id="1108f-109">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="1108f-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
