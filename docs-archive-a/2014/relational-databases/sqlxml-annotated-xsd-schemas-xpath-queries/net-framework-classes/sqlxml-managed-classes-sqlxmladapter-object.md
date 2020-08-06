---
title: SqlXmlAdapter オブジェクト (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1357ab7d070c7c2e451e31bccfda22c58eac42d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631756"
---
# <a name="sqlxmladapter-object-sqlxml-managed-classes"></a><span data-ttu-id="fd023-102">SqlXmlAdapter オブジェクト (SQLXML マネージド クラス)</span><span class="sxs-lookup"><span data-stu-id="fd023-102">SqlXmlAdapter Object (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="fd023-103">このオブジェクトでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のデータセットとの対話を容易にするためのメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="fd023-103">This object provides methods that facilitate interaction with the dataset in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="fd023-104">実際のサンプルについては、「 [.Net 環境での SQLXML 機能へのアクセス](accessing-sqlxml-functionality-in-the-net-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd023-104">For a working sample, see [Accessing SQLXML Functionality in the .NET Environment](accessing-sqlxml-functionality-in-the-net-environment.md).</span></span>  
  
 <span data-ttu-id="fd023-105">SqlXmlAdapter オブジェクトは、次のメソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fd023-105">The SqlXmlAdapter object supports these methods:</span></span>  
  
 <span data-ttu-id="fd023-106">void の Fill (DataSet ds)</span><span class="sxs-lookup"><span data-stu-id="fd023-106">void Fill(DataSet ds)</span></span>  
 <span data-ttu-id="fd023-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から取得した XML データを .NET Framework のデータセットに格納します。</span><span class="sxs-lookup"><span data-stu-id="fd023-107">Fills the dataset in the .NET Framework with the XML data retrieved from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="fd023-108">void 更新 (データセット ds)</span><span class="sxs-lookup"><span data-stu-id="fd023-108">void Update(DataSet ds)</span></span>  
 <span data-ttu-id="fd023-109">データセットのデータから、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="fd023-109">Applies updates to records in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from the data in the dataset.</span></span>  
  
 <span data-ttu-id="fd023-110">SqlXmlAdapter オブジェクトは、次のコンストラクターをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="fd023-110">The SqlXmlAdapter object supports these constructors:</span></span>  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a><span data-ttu-id="fd023-111">参照</span><span class="sxs-lookup"><span data-stu-id="fd023-111">See Also</span></span>  
 <span data-ttu-id="fd023-112">[SqlXmlCommand オブジェクト &#40;SQLXML マネージクラス&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span><span class="sxs-lookup"><span data-stu-id="fd023-112">[SqlXmlCommand Object &#40;SQLXML Managed Classes&#41;](sqlxml-4-0-net-framework-support-managed-classes.md) </span></span>  
 [<span data-ttu-id="fd023-113">SqlXmlParameter オブジェクト &#40;SQLXML マネージクラス&#41;</span><span class="sxs-lookup"><span data-stu-id="fd023-113">SqlXmlParameter Object &#40;SQLXML Managed Classes&#41;</span></span>](sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
