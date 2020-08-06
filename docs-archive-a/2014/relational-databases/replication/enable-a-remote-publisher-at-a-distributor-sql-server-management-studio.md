---
title: ディストリビューターでのリモート パブリッシャーの有効化 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06c85924731b79e8b3c79cfbcc354b5bedf69b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632364"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a><span data-ttu-id="f8520-102">ディストリビューターでのリモート パブリッシャーの有効化 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f8520-102">Enable a Remote Publisher at a Distributor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f8520-103">**[パブリッシャー]** ページでパブリッシャーを有効にし、リモート ディストリビューターを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8520-103">Enable a Publisher to use a remote Distributor on the **Publishers** page.</span></span> <span data-ttu-id="f8520-104">このページは、ディストリビューションの構成ウィザードおよび **[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスにあります。</span><span class="sxs-lookup"><span data-stu-id="f8520-104">This page is available in the Configure Distribution Wizard and the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="f8520-105">ウィザードとダイアログ ボックスのアクセス方法については、「[パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)」と「[ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8520-105">For more information about using the wizard and accessing the dialog box, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a><span data-ttu-id="f8520-106">ディストリビューションの構成ウィザードでパブリッシャーを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f8520-106">To enable a Publisher in the Configure Distribution Wizard</span></span>  
  
1.  <span data-ttu-id="f8520-107">ディストリビューションの構成ウィザードの **[パブリッシャー]** ページで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-107">On the **Publishers** page of the Configure Distribution Wizard, click **Add**.</span></span>  
  
2.  <span data-ttu-id="f8520-108">**[SQL Server パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-108">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="f8520-109">Oracle パブリッシャーを有効にしてディストリビューターを使用する方法については、「 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8520-109">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="f8520-110">**[サーバーへの接続]** ダイアログ ボックスで、リモート ディストリビューターを使用するパブリッシャーの接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-110">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="f8520-111">**[ディストリビューター パスワード]** ページの **[パスワード]** テキスト ボックスおよび **[パスワードの確認入力]** テキスト ボックスで、 **distributor_admin** アカウントの複雑なパスワードを指定します。レプリケーションでは、このアカウントを使用してパブリッシャーからディストリビューターに接続し、管理タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8520-111">On the **Distributor Password** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="f8520-112">パブリッシャーの設定を表示および変更するには、プロパティ ボタン **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-112">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a><span data-ttu-id="f8520-113">[ディストリビューターのプロパティ] ダイアログ ボックスでパブリッシャーを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f8520-113">To enable a Publisher in the Distributor Properties dialog box</span></span>  
  
1.  <span data-ttu-id="f8520-114">**[ディストリビューターのプロパティ - \<Distributor>]** ダイアログ ボックスの **[パブリッシャー]** ページで、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-114">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="f8520-115">**[SQL Server パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-115">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="f8520-116">Oracle パブリッシャーを有効にしてディストリビューターを使用する方法については、「 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8520-116">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="f8520-117">**[サーバーへの接続]** ダイアログ ボックスで、リモート ディストリビューターを使用するパブリッシャーの接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-117">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="f8520-118">**[パブリッシャー]** ページの **[パスワード]** テキスト ボックスおよび **[パスワードの確認入力]** テキスト ボックスで、 **distributor_admin** アカウントの複雑なパスワードを指定します。レプリケーションでは、このアカウントを使用してパブリッシャーからディストリビューターに接続し、管理タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8520-118">On the **Publishers** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="f8520-119">パブリッシャーの設定を表示および変更するには、プロパティ ボタン **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f8520-119">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f8520-120">参照</span><span class="sxs-lookup"><span data-stu-id="f8520-120">See Also</span></span>  
 <span data-ttu-id="f8520-121">[パブリッシングとディストリビューションの構成](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="f8520-121">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="f8520-122">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="f8520-122">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="f8520-123">ディストリビューターのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f8520-123">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
