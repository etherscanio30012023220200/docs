---
title: Restricting the retention period for codespaces
shortTitle: Restrict the retention period
intro: You can set a maximum retention period for any codespaces owned by your organization.
product: '{% data reusables.gated-features.codespaces %}'
permissions: 'To manage retention constraints for an organization''s codespaces, you must be an owner of the organization.'
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
---

## Visão Geral

{% data variables.product.prodname_codespaces %} are automatically deleted after they have been stopped and have remained inactive for a defined number of days. The retention period for each codespace is set when the codespace is created and does not change.

Everyone who has access to {% data variables.product.prodname_github_codespaces %} can configure a retention period for the codespaces they create. The initial setting for this retention period is 30 days. Individual users can set this period within the range 0-30 days. For more information, see "[Configuring automatic deletion of your codespaces](/codespaces/customizing-your-codespace/configuring-automatic-deletion-of-your-codespaces)."

As an organization owner, you may want to configure constraints on the maximum retention period for codespaces created for the repositories owned by your organization. This can help you to limit the storage costs associated with codespaces that are stopped and then left unused until they are automatically deleted. For more information about storage charges, see "[About billing for Codespaces](/billing/managing-billing-for-github-codespaces/about-billing-for-codespaces#codespaces-pricing)." You can set a maximum retention period for all, or for specific, repositories owned by your organization.

### Definindo políticas específicas da organização e do repositório

Ao criar uma política, você define se ela se aplica a todos os repositórios da organização ou apenas a repositórios específicos. If you create an organization-wide policy with a codespace retention constraint, then the retention constraints in any policies that are targeted at specific repositories should be shorter than the restriction configured for the entire organization, or they will have no effect. The shortest retention period - in an organization-wide policy, a policy targeted at specified repositories, or in someone's personal settings - is applied.

If you add an organization-wide policy with a retention constraint, you should set the retention period to the longest acceptable period. You can then add separate policies that set the maximum retention to a shorter period for specific repositories in your organization.

## Adding a policy to set a maximum codespace retention period

{% data reusables.profile.access_org %}
{% data reusables.profile.org_settings %}
{% data reusables.codespaces.codespaces-org-policies %}
1. Click **Add constraint** and choose **Retention period**.

   ![Add a constraint for retention periods](/assets/images/help/codespaces/add-constraint-dropdown-retention.png)

1. Clique {% octicon "pencil" aria-label="The edit icon" %} para editar a restrição.

   ![Editar a restrição de tempo limite](/assets/images/help/codespaces/edit-timeout-constraint.png)

1. Enter the maximum number of days codespaces can remain stopped before they are automatically deleted, then click **Save**.

   ![Set the retention period in days](/assets/images/help/codespaces/maximum-days-retention.png)

   {% note %}

   **Atenção**:
   * A day, in this context, is a 24-hour period, beginning at the time of day when the codespace was stopped.
   * The valid range is 0-30 days.
   * Setting the period to `0` will result in codespaces being immediately deleted when they are stopped, or when they timeout due to inactivity.

   {% endnote %}

{% data reusables.codespaces.codespaces-policy-targets %}
1. Se você quiser adicionar outra restrição à política, clique em **Adicionar restrição** e escolha outra restrição. For information about other constraints, see "[Restricting access to machine types](/codespaces/managing-codespaces-for-your-organization/restricting-access-to-machine-types)," "[Restricting the visibility of forwarded ports](/codespaces/managing-codespaces-for-your-organization/restricting-the-visibility-of-forwarded-ports)," and "[Restricting the idle timeout period](/codespaces/managing-codespaces-for-your-organization/restricting-the-idle-timeout-period)."
1. After you've finished adding constraints to your policy, click **Save**.

The policy will be applied to all new codespaces that are created.

## Editando uma política

Você pode editar uma política existente. Por exemplo, você deve adicionar ou remover restrições de uma política.

The retention period constraint is only applied to codespaces when they are created. Editing a policy has no effect on existing codespaces.

1. Exibir a página "Políticas de codespaces". For more information, see "[Adding a policy to set a maximum codespace retention period](#adding-a-policy-to-set-a-maximum-codespace-retention-period)."
1. Clique no nome da política que você deseja editar.
1. Faça as alterações necessárias e, em seguida, clique em **Salvar**.

## Excluindo uma política

You can delete a policy at any time. Deleting a policy has no effect on existing codespaces.

1. Exibir a página "Políticas de codespaces". For more information, see "[Adding a policy to set a maximum codespace retention period](#adding-a-policy-to-set-a-maximum-codespace-retention-period)."
1. Clique no botão excluir à direita da política que você deseja excluir.

   ![O botão de excluir uma política](/assets/images/help/codespaces/policy-delete.png)