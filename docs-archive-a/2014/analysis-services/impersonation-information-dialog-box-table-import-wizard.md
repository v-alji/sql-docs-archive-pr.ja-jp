---
title: '[権限借用情報] ダイアログボックス (テーブルのインポートウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5300f8b6106a7f29f51018b4e039c2a8c28aa729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712606"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a><span data-ttu-id="8a32f-102">[権限借用情報] ダイアログ ボックス (テーブル インポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="8a32f-102">Impersonation Information Dialog Box (Table Import Wizard)</span></span>
  <span data-ttu-id="8a32f-103">**[権限借用情報]** ページを使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がデータ ソースに接続する際に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a32f-103">Use the **Impersonation Information** page to specify the credentials that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will use to connect to the data source.</span></span> <span data-ttu-id="8a32f-104">資格情報の偽装の詳細については、「[権限借用 &#40;SSAS 表形式&#41;](tabular-models/impersonation-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a32f-104">For more information about credentials impersonation, see [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8a32f-105">Options</span><span class="sxs-lookup"><span data-stu-id="8a32f-105">Options</span></span>  
 <span data-ttu-id="8a32f-106">**[特定の Windows ユーザー名とパスワード]**</span><span class="sxs-lookup"><span data-stu-id="8a32f-106">**Specific Windows user name and password**</span></span>  
 <span data-ttu-id="8a32f-107">表形式モデルで指定した Windows ユーザー アカウントのセキュリティ資格情報を使用するには、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="8a32f-107">Select this option to have the tabular model use the security credentials of a specified Windows user account.</span></span>  
  
 <span data-ttu-id="8a32f-108">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="8a32f-108">**User name**</span></span>  
 <span data-ttu-id="8a32f-109">使用するユーザー アカウントのドメインと名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8a32f-109">Type the domain and name of the user account to be used.</span></span> <span data-ttu-id="8a32f-110">次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a32f-110">Use the following format:</span></span>  
  
 <span data-ttu-id="8a32f-111">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="8a32f-111">*\<Domain name>* **\\** *\<User account name>*</span></span>  
  
 <span data-ttu-id="8a32f-112">このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="8a32f-112">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="8a32f-113">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="8a32f-113">**Password**</span></span>  
 <span data-ttu-id="8a32f-114">テーブル モデルで使用するユーザー アカウントのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="8a32f-114">Type the password of the user account to be used by the Tabular model.</span></span>  
  
 <span data-ttu-id="8a32f-115">このオプションは、 **[特定のユーザー名とパスワードを使用する]** がオンになっている場合にのみ有効になります。</span><span class="sxs-lookup"><span data-stu-id="8a32f-115">This option is enabled only if **Use a specific name and password** is selected.</span></span>  
  
 <span data-ttu-id="8a32f-116">**サービス アカウント**</span><span class="sxs-lookup"><span data-stu-id="8a32f-116">**Service account**</span></span>  
 <span data-ttu-id="8a32f-117">このオプションを選択すると、モデルを管理する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サービスに関連付けられているセキュリティ資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8a32f-117">Select this option to use the security credentials associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a32f-118">参照</span><span class="sxs-lookup"><span data-stu-id="8a32f-118">See Also</span></span>  
 [<span data-ttu-id="8a32f-119">権限借用 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="8a32f-119">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)  
  
  
