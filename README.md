# MVC_ActionFilterAttribute

Capture Controller/Action Route and HTTP values

[APILoggingAttribute]  - Add this Attribute to any controller / action you want to capture request from
[HttpGet]
[Route("api/getxxxx")]
public async Task<IActionResult> getxxx()
        { 
            return Json("xxxxx");
        }

public class APILoggingAttribute : ActionFilterAttribute
    {
        public override void OnActionExecuting(ActionExecutingContext filterContext)
        {
            //Use the request and route data objects to grab your data
            
            string controller = filterContext.RouteData.Values["controller"].ToString();
            string action = filterContext.RouteData.Values["action"].ToString();
            var headers = filterContext.HttpContext.Request.Headers;
            
            //string userIP = httpContext.Request.UserHostAddress;
            //string userName = httpContext.User.Identity.Name;
            //string reqType = httpContext.Request.RequestType;
            //string reqData = GetRequestData(httpContext);          

            base.OnActionExecuting(filterContext);

        }     
    }
