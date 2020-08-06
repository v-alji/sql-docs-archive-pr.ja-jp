---
title: 高度な接続プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8dc844d1fdfb1e82f0ffa8de93a6a1060ef190cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642946"
---
# <a name="advanced-connection-properties"></a><span data-ttu-id="9f1da-102">高度な接続プロパティ</span><span class="sxs-lookup"><span data-stu-id="9f1da-102">Advanced Connection Properties</span></span>
  <span data-ttu-id="9f1da-103">**[高度な接続プロパティ]** ダイアログ ボックスを使用すると、接続文字列に接続パラメーターをさらに追加できます。</span><span class="sxs-lookup"><span data-stu-id="9f1da-103">Use the **Advanced Connection Properties** dialog box to add more connection parameters to the connection string.</span></span>  
  
 <span data-ttu-id="9f1da-104">追加の接続パラメーターには、使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース インスタンスでサポートされる任意の ODBC 接続パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9f1da-104">The additional connection parameters can be any ODBC connection parameter that is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database instance you are using.</span></span>  
  
 <span data-ttu-id="9f1da-105">**[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server への接続]** ダイアログ ボックスで選択したパラメーターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9f1da-105">The parameters added using the **Advanced Connection Properties** dialog box are added to the parameters selected in the **Connect to SQL Server** dialog box.</span></span>  
  
 <span data-ttu-id="9f1da-106">指定した各パラメーターの最後のインスタンスは、そのパラメーターの前のインスタンスをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9f1da-106">The last instance of each parameter provided overrides any previous instances of the parameter.</span></span> <span data-ttu-id="9f1da-107">**[高度な接続パラメーター]** ダイアログ ボックスを使用して追加したパラメーターは、 **[SQL Server 接続]** ダイアログ ボックスで指定したパラメーターの後に続き、それらのパラメーターを置換します。</span><span class="sxs-lookup"><span data-stu-id="9f1da-107">Parameters added using the **Advanced Connection Parameters** dialog box follow and replace the parameters provided in the **SQL Server Connection** dialog box.</span></span> <span data-ttu-id="9f1da-108">たとえば、 **[SQL Server 接続]** ダイアログ ボックスの [サーバー名] で「SERVER1」と指定し、 **[追加の接続パラメーター]** ページで「;SERVER=SERVER2」と指定した場合、SERVER2 に接続されます。</span><span class="sxs-lookup"><span data-stu-id="9f1da-108">For example, if the **SQL Server Connection** dialog box specifies SERVER1 as the Server name, and the **Additional Connection Parameters** page contains ;SERVER=SERVER2, the connection will be made to SERVER2.</span></span>  
  
 <span data-ttu-id="9f1da-109">**[高度な接続プロパティ]** ダイアログ ボックスを使用して追加したパラメーターは、プレーンテキストとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="9f1da-109">Parameters added using the **Advanced Connection Properties** dialog box are passed as plain text.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f1da-110">**[高度な接続プロパティ]** ダイアログ ボックスにはログイン資格情報を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="9f1da-110">Do not include login credentials in the **Advanced Connection Properties** dialog box.</span></span> <span data-ttu-id="9f1da-111">このダイアログ ボックスで指定したパラメーターは、ネットワーク経由で渡されるときに暗号化されません。</span><span class="sxs-lookup"><span data-stu-id="9f1da-111">They will not be encrypted when they are passed across the network.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f1da-112">参照</span><span class="sxs-lookup"><span data-stu-id="9f1da-112">See Also</span></span>  
 <span data-ttu-id="9f1da-113">[CDC デザイナー コンソールへのアクセス](access-the-cdc-designer-console.md) </span><span class="sxs-lookup"><span data-stu-id="9f1da-113">[Access the CDC Designer Console](access-the-cdc-designer-console.md) </span></span>  
 [<span data-ttu-id="9f1da-114">インスタンスの作成のための SQL Server 接続</span><span class="sxs-lookup"><span data-stu-id="9f1da-114">SQL Server Connection for Instance Creation</span></span>](sql-server-connection-for-instance-creation.md)  
  
  
