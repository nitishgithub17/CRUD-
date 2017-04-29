# CRUD-
## CREATE webservices.cs....How To perform crud operation using ASP.net
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Services;

[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
// To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line. 
// [System.Web.Script.Services.ScriptService]
public class WebService : System.Web.Services.WebService {

    public WebService () {
    }

    BAL bal;

    [WebMethod]
    public string InsertEmployee(string empname, string empsalary)
    {
        Common(empname, empsalary);
        string status = bal.Insert();

        if (status == "PASS")
            return "Employee details inserted.";
        else
            return "Employee details not inserted.";
    }

    [WebMethod]
    public string UpdateEmployee(string empname, string empsalary)
    {
        Common(empname, empsalary);
        string status = bal.Update();

        if (status == "PASS")
            return "Employee details Updated.";
        else
            return "Employee details not Updated.";
    }

    [WebMethod]
    public string DeleteEmployee(int id)
    {
        bal = new BAL();
        string status = bal.Delete(id);

        if (status == "PASS")
            return "Employee details deleted.";
        else
            return "Employee details not deleted.";
    }

    [WebMethod]
    public List<BAL> SelectEmployee(int id)
    {
        bal = new BAL();
        List<BAL> lstbal = bal.Select(id);

        if (lstbal != null)
            return lstbal;
        else
            return lstbal;
    }

    private void Common(string empname, string empsalary)
    {
        bal = new BAL
        {
            EmpName = empname,
            EmpSalary = empsalary
        };
    }     
}
