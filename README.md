# Welcome to Course Guard

### Project Admin: [Sanskriti Kadam] (https://github.com/Sanskriti1102)

**Overview**

Thiswebsiteallowsuserstoadd,buy,sell,andpurchasecourses,interactwithanAIchatbot
forguidance,manageuserprofiles,andviewaleaderboardthatranksusersbasedontheir
coursecompletionandachievements.Theapplicationisbuiltusingamoderntechstack:
**Next.js** forfrontend, **Node.js** forbackend,and **MongoDB** fordatastorage.

# TechStack

```
● Frontend: Next.js
● Backend: Node.js(withExpress.js)
● Database: MongoDB(NoSQL)
● Authentication: JSONWebTokens(JWT)
● Payments: Stripe(forpurchasing/sellingcourses)
● AIChatbot: IntegratedusinganNLPframeworksuchasDialogfloworOpenAI's
GPTAPI
● Leaderboard: MongoDBforstoringscores,withreal-timeupdatesusing
WebSockets
```
# Functionalities

**1.CourseManagement**

```
● AddCourse: Users(instructorrole)cancreateanduploadanewcourse.This
includesaddingcoursedetailssuchastitle,description,videos,andpricing.
● BuyCourse: Users(students)canbrowseavailablecoursesandpurchasethemvia
Stripe.
● SellCourse: Userswhohavecreatedcoursescanmonitorsalesandearningson
theirdashboard.
● PurchaseCourses: Studentscanbuycourses,andpurchasedcourseswillbe
addedtotheirprofileforeasyaccess.
```
**2.AIChatbot**

```
● Thechatbotassistsuserswithanyqueries,offerscourserecommendations,and
providesfeedbackontheplatform'susage.It’sintegratedusingNLP-based
frameworkslikeDialogfloworOpenAI’sGPTmodel.
```
**3.UserProfiles**

```
● ProfileManagement: Eachusercanmanagetheirpersonaldetails,course
enrollments,andactivityhistory.
```

```
● PurchaseHistory: Showsadetailedhistoryofallpurchasedandcompleted
courses.
● InstructorDashboard: Instructorscanmanagethecoursesthey’vecreatedand
tracksales,reviews,andfeedback.
● StudentDashboard: Studentscanviewenrolledcourses,completionrates,and
certificates.
```
**4.Leaderboard**

```
● Theleaderboardranksusersbasedonthenumberofcoursescompleted,reviews
submitted,andbadgesearned.
● Usersgainpointsthroughcompletingcoursesandengagingwiththeplatform.
```
# FrontendArchitecture(Next.js)

```
● PagesStructure:
○ /–Homepagefeaturingtopcoursesandcategories.
○ /courses–Acatalogofavailablecourseswithfiltersandsortingoptions.
○ /courses/[id]–Coursedetailpagewhereuserscanviewthecourseand
itscontent.
○ /dashboard–Userdashboardshowingprofile,enrolledcourses,and
leaderboard.
○ /chatbot–Chatbotinterfaceforuserinteraction.
● StateManagement: Using ContextAPI forglobalstate(e.g.,userauthentication)
and SWR (Stale-While-Revalidate)fordatafetchingtokeepthefrontendinsyncwith
thebackend.
● Styling: Styledusing CSSModules and TailwindCSS forrapidUIdevelopment.
```
# BackendArchitecture(Node.jswithExpress.js)

```
● APIRoutes:
○ /api/auth–HandlesuserauthenticationandJWTtokenmanagement.
○ /api/courses–HandlesCRUDoperationsforcourses.
○ /api/checkout–ManagesStripepaymentprocessingforpurchasing
courses.
○ /api/leaderboard–Managesretrievalandupdatingofleaderboarddata.
○ /api/chatbot–RoutesthatconnecttotheAIchatbotforhandling
conversations.
● UserRoles: Twomainrolesarehandledbymiddlewareforaccesscontrol:
○ Instructor
○ Student
● WebSocketIntegration: Real-timeupdatesforleaderboardscoresandnotifications
using Socket.IO.
```

# DatabaseArchitecture(MongoDB)

**UserCollection:**
json
Copycode
{

"_id": "ObjectId",
"username": "string",
"email": "string",
"passwordHash": "string",
"role": "string", // "student" or "instructor"
"coursesEnrolled": ["ObjectId"], // Array of course ids
"coursesCreated": ["ObjectId"], // Array of created course ids (if
instructor)

```
"leaderboardScore": "number"
```
}

```
●
```
**CourseCollection:**
json
Copycode
{
"_id": "ObjectId",
"title": "string",
"description": "string",
"instructor": "ObjectId", // Reference to User
"price": "number",
"videos": ["string"], // Array of video URLs
"reviews": ["ObjectId"] // Array of review ids

}

```
●
```
**LeaderboardCollection:**
json
Copycode
{

```
"userId": "ObjectId",
"score": "number"
```
}

```
● PaymentCollection: UsedfortrackingpurchasesmadeviaStripe.
```

# Authentication

```
● JWT-basedAuthentication :Protectssensitiveroutes.Usersareauthenticatedvia
JWTsgeneratedonloginandstoredinHTTP-onlycookies.Middlewareensures
properrole-basedaccesscontrol.
```
# StripeIntegration(Payments)

```
● CoursePurchaseFlow:
○ Userselectsacourseandproceedstocheckout.
○ Stripehandlessecurepaymentprocessing.
○ Afterpayment,aconfirmationemailissenttotheuser,andthecourseis
addedtotheirprofile.
```
# AIChatbot

```
● NaturalLanguageProcessing(NLP): ThechatbotispoweredbyNLPframeworks
suchas Dialogflow or OpenAI APIs.
● Features: Userscanaskquestionsrelatedtocourses,receiverecommendations,
andevengetsupportforplatformnavigation.
```
# Leaderboard

```
● Usersaccumulatepointsforcompletingcourses,providingreviews,andother
activities.
● Leaderboarddataisdisplayedontheuserdashboard,anditupdatesinreal-time
usingWebSockets.
```
# DeploymentandScaling

```
● FrontendDeployment: Deployedon Vercel ,whichisoptimizedforNext.js
applications.
● BackendDeployment: Hostedon AWS or Heroku forscalability.
● Database: Managedwith MongoDBAtlas ,acloud-basedNoSQLdatabase.
```

# FutureEnhancements

```
● GamificationFeatures: Addingbadges,coursestreaks,andrewardsforenhanced
userengagement.
● AdvancedAIFeatures: Expandingthechatbot'scapabilitieswithmorepersonalized
recommendationsandadaptivelearningpaths.
● CourseRating&Feedback: Allowstudentstoprovideratingsandcommentsonthe
coursesthey'vecompleted.
```

