---
title: パブリッシャー | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 879fa3cc2ecadf56914928c6ae83600f513f6ddb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630894"
---
# <a name="publishers"></a><span data-ttu-id="c52c6-102">[ディストリビューターのプロパティ]</span><span class="sxs-lookup"><span data-stu-id="c52c6-102">Publishers</span></span>
  <span data-ttu-id="c52c6-103">他のパブリッシャーにこのディストリビューターの使用許可を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="c52c6-103">You can give permission for other Publishers to use this Distributor.</span></span> <span data-ttu-id="c52c6-104">パブリッシャーがサーバーをパブリッシャーのリモート ディストリビューターとして使用しても、そのサーバーがパブリッシャーにならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c52c6-104">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="c52c6-105">パブリッシャーに接続し、パブリッシュするための構成を行って、このサーバーをディストリビューターとして選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c52c6-105">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="c52c6-106">パブリケーションの新規作成ウィザードを使用して、パブリッシャーを構成し、ディストリビューターを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c52c6-106">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="c52c6-107">パブリッシャーとして選択したサーバーでは、このウィザードの **[ディストリビューション データベース]** ページで指定したディストリビューション データベースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c52c6-107">The servers you select as Publishers will use the distribution database specified on the **Distribution Database** page of this wizard.</span></span> <span data-ttu-id="c52c6-108">他のディストリビューション データベースを使用する場合には、この時点でパブリッシャーを有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="c52c6-108">If you want to use a different distribution database, do not enable the Publisher at this time.</span></span> <span data-ttu-id="c52c6-109">代わりに、ディストリビューションの構成ウィザードの終了後に、 **[ディストリビューターのプロパティ]** ダイアログ ボックスを使用してパブリッシャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c52c6-109">Instead, use the **Distributor Properties** dialog box to add Publishers after you complete the Configure Distribution Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c52c6-110">オプション</span><span class="sxs-lookup"><span data-stu-id="c52c6-110">Options</span></span>  
 <span data-ttu-id="c52c6-111">**[パブリッシャー]**</span><span class="sxs-lookup"><span data-stu-id="c52c6-111">**Publishers**</span></span>  
 <span data-ttu-id="c52c6-112">このディストリビューターの使用を許可するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="c52c6-112">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="c52c6-113">その他のプロパティを表示し、設定するには、[パブリッシャー] の横にあるプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c52c6-113">Click the properties button (**...**) next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="c52c6-114">**追加**</span><span class="sxs-lookup"><span data-stu-id="c52c6-114">**Add**</span></span>  
 <span data-ttu-id="c52c6-115">許可するサーバーが一覧に表示されていない場合には、 **[追加]** をクリックして、使用できるパブリッシャーの一覧に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーまたは Oracle パブリッシャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c52c6-115">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c52c6-116">参照</span><span class="sxs-lookup"><span data-stu-id="c52c6-116">See Also</span></span>  
 <span data-ttu-id="c52c6-117">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="c52c6-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="c52c6-118">[パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="c52c6-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="c52c6-119">[View and Modify Distributor and Publisher Properties (ディストリビューターとパブリッシャーのプロパティの表示および変更)](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c52c6-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="c52c6-120">パブリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="c52c6-120">Create a Publication</span></span>](publish/create-a-publication.md)  
  
  
