# MyJiraScripts
Some groovy scripts that are useful inside jira


#Get form value for Security levels field ID.

import com.atlassian.jira.component.ComponentAccessor
import com.atlassian.jira.issue.security.IssueSecurityLevelManager
import com.atlassian.jira.issue.security.IssueSecuritySchemeManager

def issueSecuritySchemeManager = ComponentAccessor.getComponent(IssueSecuritySchemeManager)
def issueSecurityLevelManager = ComponentAccessor.getComponent(IssueSecurityLevelManager)

def schemeFromName = issueSecuritySchemeManager.getSchemeObjects().find { it.name == "Name of the Security Scheme" }
def schemeFromProject = issueSecuritySchemeManager.getSchemeFor(ComponentAccessor.projectManager.getProjectByCurrentKey("Name of the project it belongs to"))

def securityLvl = issueSecurityLevelManager.getIssueSecurityLevels(schemeFromName.id).find { it ->
    it.name == "Name of the security Level"
}?.id
