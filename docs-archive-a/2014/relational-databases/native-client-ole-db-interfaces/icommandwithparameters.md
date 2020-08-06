---
title: ICommandWithParameters | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 66644c70-def7-46d8-8c47-b883292a0288
author: rothja
ms.author: jroth
ms.openlocfilehash: df3103181b3cad772e7d1c73068b8864bf591b73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644455"
---
# <a name="icommandwithparameters"></a><span data-ttu-id="57ec6-102">ICommandWithParameters</span><span class="sxs-lookup"><span data-stu-id="57ec6-102">ICommandWithParameters</span></span>
  <span data-ttu-id="57ec6-103">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降のデータベース エンジンの機能強化により、ICommandWithParameters::GetParameterInfo で、期待される結果のより正確な記述を取得できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="57ec6-103">Improvements in the database engine beginning with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow ICommandWithParameters::GetParameterInfo to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="57ec6-104">結果がより正確になり、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で CommandWithParameters::GetParameterInfo から返される値とは異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57ec6-104">These more accurate results may differ from the values returned by CommandWithParameters::GetParameterInfo in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="57ec6-105">詳細については、「[メタデータの検出](../native-client/features/metadata-discovery.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57ec6-105">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="57ec6-106">また、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降で、ICommandWithParameters::SetParameterInfo を呼び出す際、*pwszName* パラメーターに渡される値は有効な識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="57ec6-106">Also beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], when calling ICommandWithParameters::SetParameterInfo, the value passed to the *pwszName* parameter must be a valid identifier.</span></span> <span data-ttu-id="57ec6-107">詳細については、「[データベース識別子](../databases/database-identifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57ec6-107">For more information, see [Database Identifiers](../databases/database-identifiers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ec6-108">参照</span><span class="sxs-lookup"><span data-stu-id="57ec6-108">See Also</span></span>  
 [<span data-ttu-id="57ec6-109">インターフェイス &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="57ec6-109">Interfaces &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
