---
title: ストアド プロシージャの実行 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e6ce951f343002feea5aa793d0cc2092422b819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738197"
---
# <a name="running-stored-procedures-ole-db"></a><span data-ttu-id="5f1c1-102">ストアド プロシージャの実行 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="5f1c1-102">Running Stored Procedures (OLE DB)</span></span>
  <span data-ttu-id="5f1c1-103">ステートメントの実行時、データ ソースに対して (クライアント アプリケーション内で直接ステートメントを実行または準備せずに) ストアド プロシージャを呼び出すと、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-103">When executing statements, calling a stored procedure on the data source (instead of executing or preparing a statement in the client application directly) can provide:</span></span>  
  
-   <span data-ttu-id="5f1c1-104">パフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-104">Higher performance.</span></span>  
  
-   <span data-ttu-id="5f1c1-105">ネットワーク オーバーヘッドの軽減。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-105">Reduced network overhead.</span></span>  
  
-   <span data-ttu-id="5f1c1-106">一貫性の向上</span><span class="sxs-lookup"><span data-stu-id="5f1c1-106">Better consistency.</span></span>  
  
-   <span data-ttu-id="5f1c1-107">正確性の向上</span><span class="sxs-lookup"><span data-stu-id="5f1c1-107">Better accuracy.</span></span>  
  
-   <span data-ttu-id="5f1c1-108">機能の追加。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-108">Added functionality.</span></span>  
  
 <span data-ttu-id="5f1c1-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアドプロシージャがデータを返すために使用する3つのメカニズムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports three of the mechanisms that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stored procedures use to return data:</span></span>  
  
-   <span data-ttu-id="5f1c1-110">プロシージャ内のすべての SELECT ステートメントで結果セットを生成する。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-110">Every SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="5f1c1-111">プロシージャが出力パラメーターによってデータを返すことができる。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-111">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="5f1c1-112">プロシージャに整数のリターン コードを含めることができる。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-112">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="5f1c1-113">アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-113">The application must be able to handle all of these outputs from stored procedures.</span></span>  
  
 <span data-ttu-id="5f1c1-114">結果の処理中には、さまざまな OLE DB プロバイダーからさまざまなタイミングで出力パラメーターと戻り値が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-114">Different OLE DB providers return output parameters and return values at different times during result processing.</span></span> <span data-ttu-id="5f1c1-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、ストアドプロシージャによって返された結果セットをコンシューマーが取得またはキャンセルするまで、出力パラメーターとリターンコードは提供されません。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-115">In case of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the output parameters and return codes are not supplied until after the consumer has retrieved or canceled the result sets returned by the stored procedure.</span></span> <span data-ttu-id="5f1c1-116">これらのリターン コードと出力パラメーターは、サーバーからの最後の TDS パケットで返されます。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-116">The return codes and the output parameters are returned in the last TDS packet from the server.</span></span>  
  
 <span data-ttu-id="5f1c1-117">プロバイダーでは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを使用して、出力パラメーターと戻り値を返すタイミングを報告します。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-117">Providers use the DBPROP_OUTPUTPARAMETERAVAILABILITY property to report when it returns output parameters and return values.</span></span> <span data-ttu-id="5f1c1-118">このプロパティは、DBPROPSET_DATASOURCEINFO プロパティ セットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-118">This property is in the DBPROPSET_DATASOURCEINFO property set.</span></span>  
  
 <span data-ttu-id="5f1c1-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを DBPROPVAL_OA_ATROWRELEASE に設定して、結果セットが処理または解放されるまでリターンコードと出力パラメーターが返されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="5f1c1-119">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider sets the DBPROP_OUTPUTPARAMETERAVAILABILITY property to DBPROPVAL_OA_ATROWRELEASE to indicate that return codes and output parameters are not returned until the result set is processed or released.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f1c1-120">参照</span><span class="sxs-lookup"><span data-stu-id="5f1c1-120">See Also</span></span>  
 [<span data-ttu-id="5f1c1-121">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="5f1c1-121">Stored Procedures</span></span>](stored-procedures.md)  
  
  
