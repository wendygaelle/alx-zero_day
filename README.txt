<%@ Page Title="" Language="C#" MasterPageFile="~/SiteMaster.master" AutoEventWireup="true" CodeFile="Dashboard.aspx.cs" Inherits="Dashboard" %>

<asp:Content ID="Content2" ContentPlaceHolderID="ContentPlaceHolder1" runat="Server">
    <style type="text/css">
        #toplinks input {
            position: relative;
            float: right;
            text-align: left;
            margin-bottom: 10px;
        }
    </style>
    <%
        Decimal LeaveBal = 0;
        try
        {
            var CurrentEmpDetails = (from employees in this.nav.HREmployees where employees.No == Session["username"].ToString() select employees);
            foreach (var EmpDetails in CurrentEmpDetails)
            {
                LeaveBal = Convert.ToDecimal(EmpDetails.Leave_Balance);
            }
        }
        catch (Exception Ex)
        {
            cSite.Messaging.ShowAlert(Ex.Message);
            Ex.Data.Clear();
        }
    %>

    <div class="block-header">
        <h3 style="color: white;">DASHBOARD</h3>
    </div>
    <!-- Widgets -->
    <div class="row clearfix">
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
            <div class="info-box bg-pink hover-expand-effect">
                <div class="icon">
                    <i class="material-icons">timer</i>
                </div>
                <div class="content">
                    <div class="text">LEAVE DAYS</div>
                    <div class="number count-to" data-from="0" data-to="<%= LeaveBal %>" data-speed="15" data-fresh-interval="20"></div>
                    <!--   -->
                </div>
            </div>
        </div>
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
            <div class="info-box bg-cyan hover-expand-effect">
                <div class="icon">
                    <i class="material-icons">check</i>
                </div>
                <div class="content">
                    <div class="text">APPROVED REQUEST</div>
                    <div class="number count-to" data-speed="1000" data-fresh-interval="20"></div>
                    <!-- data-from="0" data-to="7" -->
                </div>
            </div>
        </div>
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
            <div class="info-box bg-light-green hover-expand-effect">
                <div class="icon">
                    <i class="material-icons">collections_bookmark</i>
                </div>
                <div class="content">
                    <div class="text">PENDING REQUESTS</div>
                    <div class="number count-to" data-speed="1000" data-fresh-interval="20"></div>
                    <!-- data-from="0" data-to="23" -->
                </div>
            </div>
        </div>
        <div class="col-lg-3 col-md-3 col-sm-6 col-xs-12">
            <div class="info-box bg-orange hover-expand-effect">
                <div class="icon">
                    <i class="material-icons">person_add</i>
                </div>
                <div class="content">
                    <div class="text">REJECTED REQUEST </div>
                    <div class="number count-to" data-speed="1000" data-fresh-interval="20"></div>
                    <!-- data-from="0" data-to="15" -->
                </div>
            </div>
        </div>
    </div>
    <!-- #END# Widgets -->
    <!-- CPU Usage -->
    <!--<div class="row clearfix">
                <div class="col-xs-12 col-sm-12 col-md-12 col-lg-12">
                    <div class="card">
                        <div class="header">
                            <div class="row clearfix">
                                <div class="col-xs-12 col-sm-6">
                                    <h2>CPU USAGE (%)</h2>
                                </div>
                                <div class="col-xs-12 col-sm-6 align-right">
                                    <div class="switch panel-switch-btn">
                                        <span class="m-r-10 font-12">REAL TIME</span>
                                        <label>OFF<input type="checkbox" id="realtime" checked><span class="lever switch-col-cyan"></span>ON</label>
                                    </div>
                                </div> 
                            </div>
                            <ul class="header-dropdown m-r--5">
                                <li class="dropdown">
                                    <a href="javascript:void(0);" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">
                                        <i class="material-icons">more_vert</i>
                                    </a>
                                    <ul class="dropdown-menu pull-right">
                                        <li><a href="javascript:void(0);">Action</a></li>
                                        <li><a href="javascript:void(0);">Another action</a></li>
                                        <li><a href="javascript:void(0);">Something else here</a></li>
                                    </ul>
                                </li>
                            </ul>
                        </div>
                        <div class="body">
                            <div id="real_time_chart" class="dashboard-flot-chart"></div>
                        </div>
                    </div>
                </div>
            </div> -->
    <!-- #END# CPU Usage -->
    <div class="row clearfix">
        <!-- Visitors -->
        <!-- <div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
                    <div class="card">
                        <div class="body bg-pink">
                            <div class="sparkline" data-type="line" data-spot-Radius="4" data-highlight-Spot-Color="rgb(233, 30, 99)" data-highlight-Line-Color="#fff"
                                 data-min-Spot-Color="rgb(255,255,255)" data-max-Spot-Color="rgb(255,255,255)" data-spot-Color="rgb(255,255,255)"
                                 data-offset="90" data-width="100%" data-height="92px" data-line-Width="2" data-line-Color="rgba(255,255,255,0.7)"
                                 data-fill-Color="rgba(0, 188, 212, 0)">
                                12,10,9,6,5,6,10,5,7,5,12,13,7,12,11
                            </div>
                            <ul class="dashboard-stat-list">
                                <li>
                                    TODAY
                                    <span class="pull-right"><b>1 200</b> <small>USERS</small></span>
                                </li>
                                <li>
                                    YESTERDAY
                                    <span class="pull-right"><b>3 872</b> <small>USERS</small></span>
                                </li>
                                <li>
                                    LAST WEEK
                                    <span class="pull-right"><b>26 582</b> <small>USERS</small></span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div> -->
        <!-- #END# Visitors -->
        <!-- Latest Social Trends -->
        <!--<div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
                    <div class="card">
                        <div class="body bg-cyan">
                            <div class="m-b--35 font-bold">LATEST SOCIAL TRENDS</div>
                            <ul class="dashboard-stat-list">
                                <li>
                                    #socialtrends
                                    <span class="pull-right">
                                        <i class="material-icons">trending_up</i>
                                    </span>
                                </li>
                                <li>
                                    #materialdesign
                                    <span class="pull-right">
                                        <i class="material-icons">trending_up</i>
                                    </span>
                                </li>
                                <li>#adminbsb</li>
                                <li>#freeadmintemplate</li>
                                <li>#bootstraptemplate</li>
                                <li>
                                    #freehtmltemplate
                                    <span class="pull-right">
                                        <i class="material-icons">trending_up</i>
                                    </span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div> -->
        <!-- #END# Latest Social Trends -->
        <!-- Answered Tickets -->
        <!--<div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
                    <div class="card">
                        <div class="body bg-teal">
                            <div class="font-bold m-b--35">ANSWERED TICKETS</div>
                            <ul class="dashboard-stat-list">
                                <li>
                                    TODAY
                                    <span class="pull-right"><b>12</b> <small>TICKETS</small></span>
                                </li>
                                <li>
                                    YESTERDAY
                                    <span class="pull-right"><b>15</b> <small>TICKETS</small></span>
                                </li>
                                <li>
                                    LAST WEEK
                                    <span class="pull-right"><b>90</b> <small>TICKETS</small></span>
                                </li>
                                <li>
                                    LAST MONTH
                                    <span class="pull-right"><b>342</b> <small>TICKETS</small></span>
                                </li>
                                <li>
                                    LAST YEAR
                                    <span class="pull-right"><b>4 225</b> <small>TICKETS</small></span>
                                </li>
                                <li>
                                    ALL
                                    <span class="pull-right"><b>8 752</b> <small>TICKETS</small></span>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div> -->
        <!-- #END# Answered Tickets -->
    </div>
    <div class="row clearfix">
        <!-- Browser Usage -->
        <div class="col-xs-12 col-sm-12 col-md-4 col-lg-4">
            <div class="card">
                <div class="header">
                    <h2>LINKS </h2>
                    <%--<ul class="header-dropdown">
                                <li class="dropdown">
                                    <a href="javascript:void(0);" class="dropdown-toggle" role="button" aria-haspopup="true" aria-expanded="false">
                                        <i class="material-icons">more_vert</i>
                                    </a>
                                    <ul class="dropdown-menu pull-right">
                                        <li><a href="javascript:void(0);">Action</a></li>
                                        <li><a href="javascript:void(0);">Another action</a></li>
                                        <li><a href="javascript:void(0);">Something else here</a></li>
                                    </ul>
                                </li>
                            </ul>--%>
                </div>
                <div class="body">
                    <div id="donut_chart" class="dashboard-donut-chart">
                        <ul id="toplinks" style="list-style-type: none;">
                            <li style="position: relative; text-align: right;">
                                <asp:Button HorizontalContentAlignment="Left" ID="btnPersonal" runat="server" Text="Personal Details" CssClass="btn btn-sm btn-danger" Width="100%"
                                    OnClick="btnPersonal_Click" /></li>
                            <li>
                                <asp:Button ID="btnContact" runat="server" Text="Contact Details" CssClass="btn btn-sm btn-danger rbDecorated" Width="100%" OnClick="btnContact_Click" /></li>
                            <%-- <li>
                                    <asp:Button ID="btnEmergency" runat="server" Text="Emergency Contacts" CssClass="btn-danger rbDecorated" Width="100%" OnClick="btnEmergency_Click" /></li> 
                                <li>
                                    <asp:Button ID="btnDependants" runat="server" Text="Dependants" CssClass="btn-danger rbDecorated" Width="100%" OnClick="btnDependants_Click" /></li>  --%>

                            <li>
                                <asp:Button ID="btnJob" runat="server" Text="Job Details" CssClass="btn btn-sm btn-danger rbDecorated" Width="100%" OnClick="btnJob_Click" /></li>

                            <li>
                                <asp:Button ID="btnSalary" runat="server" Text="Payroll Details" CssClass="btn btn-sm btn-danger rbDecorated" Width="100%" OnClick="btnSalary_Click" /></li>

                            <li>
                                <asp:Button ID="btnQualifications" runat="server" Text="Qualifications" CssClass="btn btn-sm btn-danger rbDecorated" Width="100%" OnClick="btnQualifications_Click" /></li>

                            <li>
                                <asp:Button ID="btnMembership" runat="server" Text="Professional Memberships" CssClass="btn btn-sm btn-danger rbDecorated" Width="100%" OnClick="btnMembership_Click" /></li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
        <!-- #END# Browser Usage -->
        <!-- Task Info -->
        <div class="col-xs-12 col-sm-12 col-md-8 col-lg-8">
            <div class="card">
                <div class="header">
                    <h2>INFO</h2>
                    <ul class="header-dropdown m-r--5">
                        <li class="dropdown">
                            <a href="javascript:void(0);" class="dropdown-toggle" role="button" aria-haspopup="true" aria-expanded="false">
                                <i class="material-icons">more_vert</i>
                            </a>
                            <ul class="dropdown-menu pull-right">
                                <li><a href="javascript:void(0);">Action</a></li>
                                <li><a href="javascript:void(0);">Another action</a></li>
                                <li><a href="javascript:void(0);">Something else here</a></li>
                            </ul>
                        </li>
                    </ul>
                </div>
                <div class="body">
                    <asp:MultiView ID="MultiView2" runat="server">
                        <asp:View ID="vWDependants" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-users"></i>Dependants</div>
                                <div class="panel-body">
                                    <asp:GridView ID="Dependants" runat="server" Width="100%" CssClass="table table-condensed table-striped">
                                        <Columns>
                                            <asp:BoundField DataField="Relationship" HeaderText="Relationship" />
                                            <asp:BoundField DataField="SurName" HeaderText="Sur Name" />
                                            <asp:BoundField DataField="Other_Names" HeaderText="Other Names" />
                                            <asp:BoundField DataField="ID_No_Passport_No" HeaderText="ID No/Passport No" />
                                            <asp:BoundField DataField="Home_Tel_No" HeaderText="Phone Number" />
                                            <asp:BoundField DataField="Type" HeaderText="Type" />
                                        </Columns>

                                    </asp:GridView>
                                </div>
                            </div>

                        </asp:View>
                        <asp:View ID="vwPersonal" runat="server">
                            <div class="panel panel-default">
                                <div class="panel-heading"><i class="fa fa-user"></i>Personal information</div>
                                <div class="panel-body">
                                    <div class="row">
                                        <div class="col-md-12">
                                            <table class="table  table-condensed table-striped" width="100%">
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Name</strong></td>
                                                    <td><span id="spNames" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.Name %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Employee ID</strong></td>
                                                    <td><span id="spEmpID" runat="server" class="label label-warning"><%=Session["username"].ToString() %></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>ID Number</strong></td>
                                                    <td><span id="spIDNo" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.IdNumber %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Gender</strong></td>
                                                    <td><span id="spGender" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.Gender %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Marital Status</strong></td>
                                                    <td><span id="spMaritalStatus" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.MaritalStatus %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Nationality</strong></td>
                                                    <td><span id="spNationality" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.Nationality %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>County</strong></td>
                                                    <td><span id="spCounty" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.County %> --%>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Date of Birth</strong></td>
                                                    <td><span id="spDOB" runat="server" class="label label-warning"></span></td>
                                                    <%-- <%=Employee.Dob %> --%>
                                                </tr>
                                            </table>
                                        </div>

                                    </div>

                                    <asp:Button ID="btnUpdate" runat="server" Text="Update Information" ForeColor="#FF9900" Visible="false" OnClick="btnUpdate_Click" />
                                    <asp:MultiView ID="MultiView1" runat="server">
                                        <asp:View ID="updateInfo" runat="server">
                                            <div class="panel panel-default" style="width: 400px;">
                                                <div class="panel-heading">Update Personal information</div>
                                                <div class="panel-body">
                                                    <div class="form-group">
                                                        <asp:Label ID="Label2" runat="server" Text="Home Phone Number:"></asp:Label>
                                                        <asp:TextBox ID="txtPhoneNumber" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>
                                                    <div class="form-group">
                                                        <asp:Label ID="lblCellular" runat="server" Text="Cellular Phone Number:"></asp:Label>
                                                        <asp:TextBox ID="txtCellular" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>

                                                    <div class="form-group">
                                                        Personal
                                                <asp:Label ID="Label5" runat="server" Text="Email Address:"></asp:Label>
                                                        <asp:TextBox ID="txtXEmail" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>
                                                    <div class="form-group">
                                                        <asp:Label ID="Label6" runat="server" Text="City:"></asp:Label>
                                                        <asp:TextBox ID="txtCity" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>
                                                    <div class="form-group">
                                                        <asp:Label ID="Label3" runat="server" Text="Postal Address"></asp:Label>
                                                        <asp:TextBox ID="txtPostalAddress" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>
                                                    <div class="form-group">
                                                        <asp:Label ID="Label1" runat="server" Text="Postal Code"></asp:Label>
                                                        <asp:TextBox ID="txtPostalCode" runat="server" CssClass="form-control"></asp:TextBox>
                                                    </div>
                                                    <asp:Button ID="Update" runat="server" CssClass="btn btn-info" Text="Submit" OnClick="Update_Click" />
                                                </div>
                                            </div>
                                        </asp:View>
                                        <asp:View ID="View3" runat="server"></asp:View>
                                    </asp:MultiView>
                                </div>
                            </div>

                        </asp:View>
                        <asp:View ID="vwContact" runat="server">
                            <div class="panel panel-default">
                                <div class="panel-heading"><i class="fa fa-inbox"></i>Contact Details</div>
                                <div class="panel-body">
                                    <div class="row">
                                        <div class="col-md-12">
                                            <table class="table  table-condensed table-striped" width="100%">
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Address 1</strong></td>
                                                    <td><span id="spAddress1" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Address 2</strong></td>
                                                    <td><span id="spAddress2" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>City</strong></td>
                                                    <td><span id="spCity" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>County</strong></td>
                                                    <td><span id="spCounty1" runat="server" class="label label-warning"></span>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Postal Code</strong></td>
                                                    <td><span id="spPostalCode" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Country</strong></td>
                                                    <td><span id="spCountry1" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Home Telephone</strong></td>
                                                    <td><span id="spTelNo" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Mobile</strong></td>
                                                    <td><span id="spMobileNo" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Work Telephone</strong></td>
                                                    <td><span id="spWorkTel" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Company Email</strong></td>
                                                    <td><span id="spComMail" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                                <tr>
                                                    <td style="background-color: #d1c5d1"><strong>Personal Email</strong></td>
                                                    <td><span id="spPersonalMail" runat="server" class="label label-warning"></span></td>
                                                </tr>
                                            </table>
                                        </div>

                                    </div>
                                </div>
                            </div>
                        </asp:View>

                        <asp:View ID="vwJob" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-briefcase"></i>Job Details</div>
                                <div class="panel-body">
                                    <div class="row">
                                        <div class="col-md-12">
                                            <table>
                                                <tr>
                                                    <th colspan="4"><i class="fa fa-star-o"></i>Employment Commencement</th>
                                                </tr>
                                            </table>
                                            <table class="table  table-condensed table-striped" width="100%">
                                                <tr>
                                                    <td><strong>Joined Date</strong></td>
                                                    <td><span id="spJoinedDate" runat="server"></span></td>
                                                    <%-- <%=Employee.JoinedDate %> --%>
                                                    <td><strong>Probation End Date</strong></td>
                                                    <td><span id="spProbationDate" runat="server"></span></td>
                                                    <%-- <%=Employee.ProbationEndDate %> --%>
                                                </tr>
                                                <tr>
                                                    <td><strong>Date of Permanency</strong></td>
                                                    <td><span id="spDatePermancecy" runat="server"></span></td>
                                                    <%-- <%=Employee.DateOfPermancy %> --%>
                                                    <td>&nbsp;</td>
                                                    <td>&nbsp;</td>
                                                </tr>
                                            </table>
                                            <table>
                                                <tr>
                                                    <th colspan="4"><i class="fa fa-list"></i>Job Details</th>
                                                </tr>
                                            </table>
                                            <table class="table  table-condensed table-striped" width="100%">
                                                <tr>
                                                    <td><strong>Job Title</strong></td>
                                                    <td><span id="spJobTitle" runat="server"></span></td>
                                                    <%-- <%=Employee.Title %> --%>
                                                    <td><strong>Job Specification</strong></td>
                                                    <td>
                                                        <button type="button" style="margin-bottom: 0px;" class="btn btn-primary btn-sm" data-toggle="modal" data-target=".bs-example-modal-lg">Click to View</button></td>
                                                </tr>
                                                <tr>
                                                    <td><strong>Employment Status</strong></td>
                                                    <td><span id="spEmpStat" runat="server"></span></td>
                                                    <%-- <%=Employee.DateOfPermancy %> --%>
                                                    <td>&nbsp;</td>
                                                    <td>&nbsp;</td>
                                                </tr>
                                                <tr>
                                                    <td><strong>Job Category</strong></td>
                                                    <td><span id="spJobCat" runat="server"></span></td>
                                                    <%-- <%=Employee.Category %> --%>
                                                    <td><strong>Sub unit</strong></td>
                                                    <td><span id="spDpeName" runat="server"></span></td>
                                                    <%-- <%=Employee.DepartmentName %> --%>
                                                </tr>
                                                <tr>
                                                    <td><strong>Location</strong></td>
                                                    <td><span id="spCampus" runat="server"></span></td>
                                                    <%-- <%=Employee.Campus %> --%>
                                                    <td>&nbsp;</td>
                                                    <td>&nbsp;</td>
                                                </tr>
                                            </table>
                                            <table>
                                                <tr>
                                                    <th colspan="4"><i class="fa fa-clock-o"></i>Job History</th>
                                                </tr>
                                            </table>
                                            <asp:GridView ID="dgJobHistory" Width="100%" runat="server" CssClass="table table-condensed table-responsive table-striped" AutoGenerateColumns="False">
                                                <Columns>
                                                    <asp:BoundField DataField="Company_Name" HeaderText="Company Name" />
                                                    <asp:BoundField DataField="From" DataFormatString="{0:dd/MM/yy}" HeaderText="From Date" />
                                                    <asp:BoundField DataField="To_Date" DataFormatString="{0:dd/MM/yy}" HeaderText="To Date" />
                                                    <asp:BoundField DataField="Job_Title" HeaderText="Job Title" />
                                                    <asp:BoundField DataField="Key_Experience" HeaderText="Key Experience" />
                                                    <asp:BoundField DataField="Salary_On_Leaving" HeaderText="Salary On Leaving" />
                                                    <asp:BoundField DataField="Reason_For_Leaving" HeaderText="Reason for Leaving" />
                                                </Columns>
                                            </asp:GridView>
                                            <!-- Large modal -->
                                            <div class="modal fade bs-example-modal-lg" tabindex="-1" role="dialog" aria-labelledby="myLargeModalLabel">
                                                <div class="modal-dialog modal-lg" role="document">
                                                    <div class="modal-content">
                                                        <div class="modal-header">
                                                            <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
                                                            <h4 class="modal-title">Job Specifications</h4>
                                                        </div>
                                                        <div class="modal-body">
                                                            <div class="row">
                                                                <div class="col-md-12">
                                                                    <%= cSite.getJobSpecifications(Employee.JSpecification) %>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>

                                    </div>
                                </div>
                            </div>
                        </asp:View>
                        <asp:View ID="vwSalary" runat="server">
                            <div class="panel panel-default">
                                <div class="panel-heading"><i class="fa fa-inbox"></i>Payroll Details</div>
                                <div class="panel-body">
                                    <div class="row">
                                        <div class="col-md-12">
                                            <table class="table  table-condensed table-striped" width="100%">
                                                <tr>
                                                    <td>Bank Name</td>
                                                    <td><span id="spBank" runat="server"></span></td>
                                                    <%-- <%=Employee.Bank %> --%>
                                                </tr>
                                                <tr>
                                                    <td>Branch</td>
                                                    <td><span id="spBanch" runat="server"></span></td>
                                                    <%-- <%=Employee.Branch %> --%>
                                                </tr>
                                                <tr>
                                                    <td>Account Number</td>
                                                    <td><span id="spAccountNo" runat="server"></span></td>
                                                    <%--<%=Employee.AccountNo %>  --%>
                                                </tr>
                                                <tr>
                                                    <td>PIN Number</td>
                                                    <td><span id="spPin" runat="server"></span></td>
                                                    <%-- <%=Employee.PIN %> --%>
                                                </tr>
                                                <tr>
                                                    <td>NSSF Number</td>
                                                    <td><span id="spNSSF" runat="server"></span></td>
                                                    <%--  <%=Employee.NSSF %> --%>
                                                </tr>
                                                <tr>
                                                    <td>NHIF Number</td>
                                                    <td><span id="spNHIF" runat="server"></span></td>
                                                    <%-- <%=Employee.NHIF %> --%>
                                                </tr>
                                            </table>
                                        </div>

                                    </div>
                                </div>
                            </div>
                        </asp:View>
                        <asp:View ID="vwQualifications" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-users"></i>Academic Qualifications</div>
                                <div class="panel-body">
                                    <asp:GridView ID="dgQualifications" runat="server" Width="100%" CssClass="table table-condensed table-striped">
                                        <Columns>
                                            <asp:BoundField DataField="Qualification" HeaderText="Qualification" />
                                            <asp:BoundField DataField="Type" HeaderText="Type" />
                                            <asp:BoundField DataField="Institution_Name" HeaderText="Institution" />
                                            <asp:BoundField DataField="From_Date" HeaderText="From Date" DataFormatString="{0:dd/MM/yy}" />
                                            <asp:BoundField DataField="To_Date" HeaderText="To_Date" DataFormatString="{0:dd/MM/yy}" />
                                            <asp:BoundField DataField="Description" HeaderText="Description" />
                                            <asp:BoundField DataField="Description" HeaderText="Description" />
                                        </Columns>

                                    </asp:GridView>
                                </div>
                            </div>

                        </asp:View>
                        <asp:View ID="vwEmergencyContact" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-users"></i>Emergency Contacts</div>
                                <div class="panel-body">
                                    <asp:GridView ID="Kins" runat="server" Width="100%" CssClass="table table-condensed table-striped">
                                        <Columns>
                                            <asp:BoundField DataField="Relationship" HeaderText="Relationship" />
                                            <asp:BoundField DataField="SurName" HeaderText="Sur Name" />
                                            <asp:BoundField DataField="Other_Names" HeaderText="Other Names" />
                                            <asp:BoundField DataField="ID_No_Passport_No" HeaderText="ID No/Passport No" />
                                            <asp:BoundField DataField="Home_Tel_No" HeaderText="Mobile" />
                                            <asp:BoundField DataField="Office_Tel_No" HeaderText="Office Telephone" />
                                            <asp:BoundField DataField="Type" HeaderText="Type" />
                                        </Columns>

                                    </asp:GridView>
                                </div>
                            </div>
                        </asp:View>

                        <asp:View ID="vwProfessionalMembership" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-users"></i>Professional Membership</div>
                                <div class="panel-body">
                                    <asp:GridView ID="dgProfessionalMembership" runat="server" Width="100%" CssClass="table table-condensed table-striped">
                                        <Columns>
                                            <asp:BoundField DataField="Membership_No" HeaderText="Membership No" />
                                            <asp:BoundField DataField="Name_of_Body" HeaderText="Membership Body" />
                                            <asp:BoundField DataField="Date_of_Membership" HeaderText="Date of Membership" />
                                            <asp:BoundField DataField="Membership_Status" HeaderText="Membership Status" />
                                            <asp:BoundField DataField="Remarks" HeaderText="Remarks" />
                                            <asp:BoundField DataField="Subscription_Commence_Date" HeaderText="Subscription Commence Date" />
                                            <asp:BoundField DataField="Subscription_Renewal_Date" HeaderText="Subscription Renewal Date" />
                                        </Columns>

                                    </asp:GridView>
                                </div>
                            </div>

                        </asp:View>
                        <asp:View ID="View10" runat="server">
                            <div class="panel panel-warning">
                                <div class="panel-heading"><i class="fa fa-users"></i>Academic Qualifications</div>
                                <div class="panel-body">
                                    <asp:GridView ID="GridView5" runat="server" Width="100%" CssClass="table table-condensed table-striped">
                                        <Columns>
                                            <asp:BoundField DataField="Qualification" HeaderText="Qualification" />
                                            <asp:BoundField DataField="Type" HeaderText="Type" />
                                            <asp:BoundField DataField="Institution_Name" HeaderText="Institution" />
                                            <asp:BoundField DataField="From_Date" HeaderText="From Date" DataFormatString="{0:dd/MM/yy}" />
                                            <asp:BoundField DataField="To_Date" HeaderText="To_Date" DataFormatString="{0:dd/MM/yy}" />
                                            <asp:BoundField DataField="Description" HeaderText="Description" />
                                            <asp:BoundField DataField="Description" HeaderText="Description" />
                                        </Columns>

                                    </asp:GridView>
                                </div>
                            </div>

                        </asp:View>
                    </asp:MultiView>
                    <!--
                            <div class="table-responsive">
                                <table class="table table-hover dashboard-task-infos">
                                    <thead>
                                        <tr>
                                            <th>#</th>
                                            <th>Task</th>
                                            <th>Status</th>
                                            <th>Manager</th>
                                            <th>Progress</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>1</td>
                                            <td>Task A</td>
                                            <td><span class="label bg-green">Doing</span></td>
                                            <td>John Doe</td>
                                            <td>
                                                <div class="progress">
                                                    <div class="progress-bar bg-green" role="progressbar" aria-valuenow="62" aria-valuemin="0" aria-valuemax="100" style="width: 62%"></div>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>2</td>
                                            <td>Task B</td>
                                            <td><span class="label bg-blue">To Do</span></td>
                                            <td>John Doe</td>
                                            <td>
                                                <div class="progress">
                                                    <div class="progress-bar bg-blue" role="progressbar" aria-valuenow="40" aria-valuemin="0" aria-valuemax="100" style="width: 40%"></div>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>3</td>
                                            <td>Task C</td>
                                            <td><span class="label bg-light-blue">On Hold</span></td>
                                            <td>John Doe</td>
                                            <td>
                                                <div class="progress">
                                                    <div class="progress-bar bg-light-blue" role="progressbar" aria-valuenow="72" aria-valuemin="0" aria-valuemax="100" style="width: 72%"></div>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>4</td>
                                            <td>Task D</td>
                                            <td><span class="label bg-orange">Wait Approvel</span></td>
                                            <td>John Doe</td>
                                            <td>
                                                <div class="progress">
                                                    <div class="progress-bar bg-orange" role="progressbar" aria-valuenow="95" aria-valuemin="0" aria-valuemax="100" style="width: 95%"></div>
                                                </div>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>5</td>
                                            <td>Task E</td>
                                            <td>
                                                <span class="label bg-red">Suspended</span>
                                            </td>
                                            <td>John Doe</td>
                                            <td>
                                                <div class="progress">
                                                    <div class="progress-bar bg-red" role="progressbar" aria-valuenow="87" aria-valuemin="0" aria-valuemax="100" style="width: 87%"></div>
                                                </div>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                            -->
                </div>
            </div>
        </div>
        <!-- #END# Task Info -->

    </div>

</asp:Content>

