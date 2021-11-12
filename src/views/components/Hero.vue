<template>
    <section class="section section-shaped my-0">
        <div class="shape shape-style-1 shape-primary">
            <span class="span-150"></span>
            <span class="span-50"></span>
            <span class="span-50"></span>
            <span class="span-75"></span>
            <span class="span-100"></span>
            <span class="span-75"></span>
            <span class="span-50"></span>
            <span class="span-100"></span>
            <span class="span-50"></span>
            <span class="span-100"></span>
        </div>
        <div class="container shape-container d-flex align-items-center" style="height:100px">
          
            <div class="col px-0">
                <div class="row justify-content-center align-items-center">
                    <div class="col-lg-7 text-center pt-lg">
                        <h1 class="text-white mt-0 mb-9">Session Case Notes</h1>
                    </div>
                </div>
            </div>
        </div>
        <div class="profile-page">
            <section class="section-profile-cover section-shaped my-0">
                <div class="shape shape-style-1 shape-primary shape-skew alpha-4">
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </section>
            
            <section class="section section-skew">
                <div class="container" style = "margin-top: -32.8%;">
                    <card shadow class="card-profile mt--300" no-body>
                    <div class="d-flex flex-row-reverse pt-sm">
                        <base-button size="sm" type="primary" style = "height:30px; width:90px;" v-on:click="signOut">Sign Out</base-button>
                        <base-button size="sm" block type="warning" class=" mb-3 float-right" @click="modal = true" style = "height:30px; width:130px;"> Clear All Fields </base-button>
                        <router-link to="/Guideline" title="General Guideline">
                            <base-button size="sm"  type="neutral" style="height:30px; margin-right:660px">Guideline</base-button>
                        </router-link>
                        <modal :show.sync="modal" gradient="danger" modal-classes="modal-danger modal-dialog-centered">
                            <h6 slot="header" class="modal-title" id="modal-title-notification">Your attention is required</h6>
                            <div class="py-3 text-center">
                                <i class="ni ni-bell-55 ni-3x"></i>
                                <h4 class="heading mt-4">You are about to clear all fields in this form</h4>
                                <p>Are you sure you want to proceed?</p>
                            </div>

                            <template slot="footer">
                                <base-button type="white" @click="clearFields">Yes, clear all fields.</base-button>
                                <base-button type="link"
                                text-color="white"
                                class="ml-auto"
                                @click="modal = false">
                                Check again
                                </base-button>
                            </template>
                        </modal>
                        
                    </div>
                        <div class="px-4">
                            <div class="row justify-content-center">
                                <div class="col-lg-4.5 order-lg-3">
                                    <span></span>
                                    <br><br>
                                    <router-link to="/first-session" title="First Session">
                                        <base-button type="default" class="mr-4">First Session</base-button>
                                    </router-link>
                                    <router-link to="/subsequent-session" title="Subsequent Session">
                                        <base-button type="default" class="mr-4">Subsequent Session</base-button>
                                    </router-link>
                                    <router-link to="/summary" title="Summary">
                                        <base-button type="default" class="mr-4">Summary</base-button>
                                    </router-link>
                                    <!-- toggle between the sessions -->
                                </div>
                            </div>
                            <!-- form start -->
                            <form id="first-session">
                                <div class="text-center mt-5">
                                    <h2><strong>First Session Form</strong></h2>
                                    <br><br>
                                </div>
                                <div ref="client-information">
                                    <div>
                                        <h2 class="heading-title text-warning mb-0">Client Information</h2>
                                        <div class="row">
                                          <p class="ml-3"> The client's information can be automatically filled up by entering their NRIC and clicking on "Retrieve".</p>
                                        </div>
                                        <br>
                                        <div class="row">
                                            <div class="col-lg-6 col-sm-6">
                                                <div class="row">
                                                    <base-input class="col-sm-9" label="NRIC" v-model="nric" id="nric"></base-input>
                                                    <base-button size="sm " type="primary" style = "height:45px; width:105px; margin-top:31px" v-on:click="retrieveData">Retrieve</base-button>
                                                    <modal :show.sync="retrieveSuccess" gradient="primary" modal-classes="modal-danger modal-dialog-centered">
                                                      <div class="py-3 text-center">
                                                        <i class="ni ni-check-bold ni-3x"></i>
                                                        <h4 class="heading mt-4">Data Retrieved Successfully!</h4>
                                                      </div>

                                                      <template slot="footer">
                                                          <base-button type="link"
                                                                      text-color="white"
                                                                      class="ml-auto"
                                                                      @click="retrieveSuccess = false">
                                                              Close window
                                                          </base-button>
                                                      </template>
                                                    </modal>
                                                </div>
                                                <base-input label="Rank/Name" v-model="name"></base-input>
                                                <label class="mb-3" >Age</label>
                                                <base-input v-model="age"></base-input>
                                                <base-input label="Unit" v-model="unit"></base-input>
                                                <base-input label="Enlistment Date (for NSFs)" v-model = "enlistment"></base-input>
                                            </div>
                                            <div class="col-lg-6 col-sm-6">
                                                <base-input label="Marital Status" v-model="maritalstatus"></base-input>
                                                <base-input label="Race" v-model="race"></base-input>
                                                <label class="my-auto">Gender</label>
                                                <!-- <tabs tabNavClasses="nav-fill flex-column flex-sm-row">
                                                    <tab-pane title="Male"></tab-pane>
                                                    <tab-pane title="Female"></tab-pane>
                                                </tabs> -->
                                                <div class="row justify-content-left">
                                                    <base-checkbox style="margin-left:4%;margin-top:5%;margin-bottom:6%" v-model="gender.male">Male</base-checkbox>
                                                    <base-checkbox style="margin-left:25%;margin-top:5%;margin-bottom:6%" v-model="gender.female">Female</base-checkbox>
                                                </div>
                                                <base-input label="Contact No" v-model="contact"></base-input>
                                                <base-input label="Expected ORD (for NSFs)" v-model = "ord"></base-input>
                                                <!-- <base-input label="Expected ORD (for NSFs)"><date-pickers></date-pickers></base-input> -->
                                            </div>
                                        </div>
                                        <label>Source of Referral</label>
                                        <div class="row justify-content-left">
                                            <base-checkbox class="my-1 ml-3 col-lg-1" v-model="sourceOfReferral.self">Self</base-checkbox>
                                            <base-checkbox class="my-1 col-lg-1" v-model="sourceOfReferral.imh">IMH</base-checkbox>
                                            <base-checkbox style="margin-right:30px" class="my-1" v-model="sourceOfReferral.supervisor">Supervisor</base-checkbox>
                                            <base-checkbox style="margin-right:30px" class="my-1" v-model="sourceOfReferral.medicalOfficer">Medical Officer</base-checkbox>
                                            <base-checkbox style="margin-right:15px" class="my-1" v-model="sourceOfReferral.others">Others:</base-checkbox>
                                            <base-input v-model="sourceOfReferral.othersInput"></base-input>
                                        </div>
                                        <div>
                                            <div class="d-flex flex-row pt-sm">
                                                <label style="margin-top:2px">Reason(s) for Referral</label><br>
                                                <base-button 
                                                size="sm" 
                                                outline 
                                                type="secondary"
                                                style="margin-left:5px ;margin-bottom:5px"
                                                v-b-popover.hover.right="'Reason(s) for referrals are indicated in the referral email sent by EBSC. This can include “stressed from tensions occurring at workplace”, “stressed from relationship problems”, “anxiety during turnouts” and so forth. .'"> ⓘ
                                                </base-button>
                                            </div>

                                              <vue-editor v-model="reasonsForReferral"></vue-editor>
                                        </div>      
                                    </div>
                                </div>
                                <br><br><br>
                                <div>
                                    <div>
                                        <div>
                                            <h2 class="heading-title text-warning mb-0">Session Information</h2>
                                            <br>
                                            <div class="row">
                                                <div class="col-lg-6 col-sm-6">
                                                    <label>Session Date</label><date-pickers></date-pickers>
                                                    <base-input label="Start Time" v-model="time" :placeholder="[[ curren_time() ]]" id="session_date"></base-input>
                                                    <base-input label="End Time"></base-input>
                                                    <!-- <vue-timepicker input-class="base-input"></vue-timepicker> -->
                                                </div>
                                                <div class="col-lg-6 col-sm-6">
                                                    <base-input label="Venue">
                                                        <select class="form-control" id="venue">
                                                            <option>Meeting Room 1</option>
                                                            <option>Meeting Room 2</option>
                                                            <option>Meeting Room 3</option>
                                                            <option>Meeting Room 4</option>
                                                            <option>Meeting Room 5</option>
                                                        </select>
                                                    </base-input>
                                                    <!-- <base-input placeholder="Counsellor(s)"></base-input> -->
                                                    <base-input label= "Counsellor">
                                                        <select class="form-control" id="counsellor">
                                                            <option>Abel Sim</option>
                                                            <option>Azharee Bin Arsad</option>
                                                            <option>Bryan Goh</option>
                                                            <option>Caleb Kelvin Cheang</option>
                                                            <option>Cheo Peng Seng</option>
                                                            <option>Cheryl Low </option>
                                                            <option>Clara Cheang</option>
                                                            <option>Cyrus Chng</option>
                                                            <option>Doris Low</option>
                                                            <option>Eleena</option>
                                                            <option>Faizal Mazlan</option>
                                                            <option>Ghazali Ahmad</option>
                                                            <option>Hasan Kuddos</option>
                                                            <option>Hazeeq Firoz</option>
                                                            <option>Jared Koh</option>
                                                            <option>Jumilah Julie</option>
                                                            <option>Kelvin Chang</option>
                                                            <option>Khairiyah Kassim</option>
                                                            <option>Khoo Swee Giang</option>
                                                            <option>Kuang Zhong Xuan</option>
                                                            <option>Low Hwee Lang</option>
                                                            <option>Maisya Bte Abd Karim</option>
                                                            <option>Md Ariffin Bin Haris</option>
                                                            <option>Md Halmy Md Timyati</option>
                                                            <option>Mohd Halmy Bin Timyati</option>
                                                            <option>Mohd Shariff Bin Syed Mohd </option>
                                                            <option>Muhammad Tasnim Bin Zainuddin</option>
                                                            <option>Nasir Bin Ahmad</option>
                                                            <option>Nasiruddin Ghaffor</option>
                                                            <option>Ng Song Lim</option>
                                                            <option>Noor Asrik Bin Masahlan</option>
                                                            <option>Norashikin Imran</option>
                                                            <option>Nurhamizah Anwar</option>
                                                            <option>Nursyahrin</option>
                                                            <option>Poh Han Wei</option>
                                                            <option>Rafidah Mahmood</option>
                                                            <option>Raymond Choo</option>
                                                            <option>Raymond Lee</option>
                                                            <option>Razali Othman</option>
                                                            <option>Rizwan Ahmad</option>
                                                            <option>Sasi Kumar Asokuma </option>
                                                            <option>Sharifah Muslimah</option>
                                                            <option>Siti Zarinah Bte Sarip</option>
                                                            <option>Soffeyan Sabirin</option>
                                                            <option>Teo Mei Tin</option>
                                                        </select>
                                                    </base-input>
                                                </div>
                                            </div>
                                            <br><br>
                                            <div>
                                                <div class="d-flex flex-row pt-sm">
                                              <h5 class="heading-title text-warning mb-0">Observations of Presentation</h5>
                                                <base-button 
                                                size="sm" 
                                                outline 
                                                type="secondary"
                                                style="margin-left:5px ;margin-bottom:5px"
                                                v-b-popover.hover.right= "'This section allows attending counsellors to pay attention to the verbal and non-verbal behaviours. \
                                                This allows a more comprehensive cross-sectional description of the client’s mental state at a given point in time.  \
                                                When combined with biographical and historical information, it allows the counsellor to make a more accurate understanding of the presenting problems, which are required for coherent intervention. \
                                                Domains can include appearance, behaviour, mood and affect, cognition and judgment. Please refer to the annex section of the case notes template for more information. \
                                                Observing the presentation of the client could also allow you to assess potential risk of harm to themselves or others, or both.'"> ⓘ
                                                </base-button>
                                                </div>
                                              <br>
                                              <div class="row justify-content-left">
                                                  <p class="ml-3">Click on the annex button to get a guide for this section. </p>
                                                  <base-button class="ml-4" size="sm" style="height:30px" v-on:click="isAnnex = !isAnnex" >Annex</base-button>
                                              </div>
                                                  
                                              <div id="annex">
                                                  <img v-show="isAnnex" width="930px" src="./ANNEX1.png" />
                                                  <img v-show="isAnnex" width="930px" src="./ANNEX2.png" />
                                                  <img v-show="isAnnex" width="930px" src="./ANNEX3.png" />
                                              </div>
                                              <vue-editor v-model="obsOfPresentation"></vue-editor>
                                            </div>      
                                        </div>
                                    </div>
                                    <br><br><br>
                                    <div>
                                        <div>
                                            <div>
                                                <div class="d-flex flex-row pt-sm">
                                              <h5 class="heading-title text-warning mb-0">Counselling Goals</h5>
                                                <base-button 
                                                size="sm" 
                                                outline 
                                                type="secondary"
                                                style="margin-left:5px ;margin-bottom:5px"
                                                v-b-popover.hover.right= "'Counselling goals should be mutually agreed upon. Identifying a S.M.A.R.T. goal can help build a conversational tool during your session – be specific, measurable, attainable, realistic and timely in setting the goals.'"> ⓘ
                                                </base-button>
                                                </div>
                                                <p>List down client’s counselling/ therapy goals (mutually agreed) to be achieved for counselling and/or during the current session.</p>
                                              <vue-editor v-model="counsellingGoals"></vue-editor>
                                                <br><br><br><br>
                                                <h5 class="heading-title text-warning mb-0">Details Of Session</h5>
                                                <p>Details of the issues discussed during the session. Background information should include
                                                    <ul>
                                                        <li>family/ childhood background and issues, </li>
                                                        <li>educational background,</li>
                                                        <li>employment history and issues,</li>
                                                        <li>interpersonal relationships, </li>
                                                        <li>financial issues, </li>
                                                        <li>history of substance use (e.g., alcohol and drugs), </li>
                                                        <li>lifestyle issues,</li>
                                                        <li>medical history,</li>
                                                        <li>mental health history (incl. self-harm and suicide behaviours)</li>
                                                    </ul>
                                                </p>

                                              <vue-editor v-model="detailsOfSession"></vue-editor>
                                                <br><br><br>

                                                <div class="d-flex flex-row pt-sm">
                                                <h5 class="heading-title text-warning mb-0">Case Conceptualisation</h5>
                                                <base-button 
                                                size="sm" 
                                                outline 
                                                type="secondary"
                                                style="margin-left:5px ;margin-bottom:5px"
                                                v-b-popover.hover.right= "'Understanding the client’s needs helps to build a coherent plan for focused interventions. It identifies contributing (note: not causal) factors that trigger and maintain the presenting issue.  Use a framework that you may be more familiar with (e.g., biopsychosocial framework shared during P.S.L.E.) . Always check in on your case conceptualisation with EBSC, wherever possible. '"> ⓘ
                                                </base-button>
                                                </div>

                                                
                                                <p>Your assessment of the client’s key underlying issues, obstacles that prevent him / her from resolving the issues, factors that have contributed to his / her progress, personal strengths that could be leveraged to help client manage his / her issues better, perceived social support network to help client manage presenting problem(s), any suspected psychological conditions that the client may be presenting, etc.</p>

                                                <vue-editor v-model="caseConceptualisation"></vue-editor>
                                                <br><br><br><br>

                                                <h5 class="heading-title text-warning mb-0">Intervention(s) provided</h5>
                                                <p>Brief but clear summary of the intervention work that has been undertaken with the client during the session (e.g., what were the proposed plans that were agreed upon, any homework assigned to the client, etc.). If client expressed suicidal ideation, include suicide safety plan.</p>
                                                <vue-editor v-model="interventionsProvided"></vue-editor>
                                                <br><br><br><br>
                                            </div>
                                        </div>
                                    </div>
                                    <div>
                                        <h5 class="heading-title text-warning mb-0">Suicide Risk Considerations (If Relevant)</h5>
                                        <p>Indicate clients’ responses during current session, if applicable.<br>In an event that client presents with active suicidal ideation during the current session, please refer client to a Medical Centre immediately. Please ensure the safety of the client before reaching out to your Parac TL and/or EBSC, if in doubt.</p>
                                        <div><base-button v-on:click="isIntent = !isIntent">1. Intent</base-button></div>
                                        <div id="intent" v-show="isIntent">
                                            <br>
                                            <p>Verbalises thoughts of suicide</p>
                                            <textarea name="intent1" row=20 cols=95 id='verbal-intent'></textarea>
                                            <br>
                                            <p>Ambivalence towards suicide</p>
                                            <textarea name="intent2" row=20 cols=95 id='ambivalence-intent'></textarea>
                                            <br><br>
                                        </div>
                                        <br>

                                        <div><base-button v-on:click="isPlans = !isPlans" >2. Plans</base-button></div>
                                        <div id="plans" v-show="isPlans">
                                            <br>
                                            <p>Explore about suicide (e.g., research)</p>
                                            <textarea name="plan1" row=20 cols=95 id='explore-plans'></textarea>
                                            <p>Have concrete plans to attempt suicide</p>
                                            <textarea name="plan2" row=20 cols=95 id='concrete-plans'></textarea>
                                            <p>Have access to lethal means for suicide</p>
                                            <textarea name="plan3" row=20 cols=95 id='lethal-means'></textarea>
                                            <br><br>
                                        </div>
                                        <br>

                                        <div><base-button v-on:click="isResources = !isResources">3. Resources</base-button></div>
                                        <div id="resources" v-show="isResources">
                                            <br>
                                            <p>Strength of social support</p>
                                            <textarea name="resources1" row=20 cols=95 id='social-resource'></textarea>
                                            <p>Problem solving skills</p>
                                            <textarea name="resources2" row=20 cols=95 id='skills-resource'></textarea>
                                            <br><br>
                                        </div>
                                        <br>

                                        <div><base-button v-on:click="isPastAttempt = !isPastAttempt">4. Past Attempt</base-button></div>
                                        <div id="pastAttempts" v-show="isPastAttempt">
                                            <br>
                                            <p>History of past suicide attempts</p>
                                            <textarea name="pastAttempt" row=20 cols=95 id='suicide-attempt'></textarea>
                                            <br><br>
                                        </div>
                                        <br>

                                        <div><base-button v-on:click="isMentalHealth = !isMentalHealth">5. Mental Health</base-button></div>
                                        <div id="mentalHealth" v-show="isMentalHealth">
                                            <br>
                                            <p>Presence of mental health illness</p>
                                            <textarea name="mentalHealth" row=20 cols=95 id='mental-health'></textarea>
                                            <br><br>
                                        </div>
                                        <br><br>
                                        <h5>Overall Risk Level</h5>
                                        <div class="row justify-content-center">
                                            <div class="col-lg-3" id="risk_level">
                                                <br>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="riskLevel.low">Low</base-checkbox><br>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="riskLevel.medium">Moderate</base-checkbox><br>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="riskLevel.high">High</base-checkbox>
                                            </div>

                                            <div class="col-lg-9 mt-5 mt-lg-0">
                                                <br>
                                                <card shadow>
                                                    <p class="small mb-1">It is recommended that suicide risk is managed during and immediately after the session. </p>
                                                    <p class="small mb-1">If there is a high risk of suicide, attending aracounsellors/ counsellors should inform and discuss with the unit supervisor on the safety plan.</p>
                                                    <p class="small mb-1">The safety plan can include seeking medical attention from the SCDF Medical Centre, conveyance to IMH or the nearest A&E or a restructured hospital. </p>
                                                    <p class="small mb-1">When in doubt, please reach out to EBSC or the SCDF Counselling Helpline (1800 286 6666).</p>
                                              </card>
                                            </div>
                                        </div>
                                    </div>
                                    <br><br>
                                    <div>
                                        <h5 class="heading-title text-warning mb-0">Follow-up Plans</h5>
                                        <p>Indicate your follow-up plans for the case.</p>
                                        <br>
                                        <h6>Case management</h6>
                                        <small>To update or reach out to the following:</small>
                                        <br><br>
                                        <div class="row justify-content-center">
                                            <div class="col-lg-3" id="case_management">
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="followUpPlans.client">Client’s supervisors</base-checkbox>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="followUpPlans.unit">Unit Paracounsellor to monitor</base-checkbox>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="followUpPlans.medical">Medical Officer</base-checkbox>
                                                <base-checkbox class="mb-3 flex-column flex-md-row" v-model="followUpPlans.other">Other agencies</base-checkbox>
                                            </div>

                                            <div class="col-lg-9 mt-5 mt-lg-0">
                                                <card shadow>
                                                    <p class="small mb-1">Apart from suicide risk, the following are common areas of update (subjected to client’s consent):</p>
                                                    <p class="small mb-1">- Mental health condition</p>
                                                    <p class="small mb-1">- Coping strategies</p>
                                                    <p class="small mb-1">- Recommended work arrangements</p>
                                                    <p class="small mb-1">Note: Advocacy for posting is discouraged during counselling sessions. Please contact EBSC for further discussion prior to updating supervisors if a change in posting is recommended.</p>
                                                </card>
                                            </div>
                                        </div>
                                        <br>
                           
                                        <br>
                                        <h6>Follow-up Plans</h6>
                                        <p class="small">Include next date of session, if applicable. <br>If no follow up is required, state reasons for closure. <br>If case is required for handover, please append handover form upon submission of case notes.</p>
                                        <label>Next Session Date</label>
                                        <base-input class="row justify-content-left col-lg-4"><date-pickers></date-pickers></base-input>
                                        <label>Reason(s) for Closure</label><br>
                                        <vue-editor v-model="reasonsForClosure"></vue-editor>
                                    </div>
                                </div>
                        <br><br><br>
                        <!-- <div>
                            <h5 class="heading-title text-warning mb-0">Summary</h5><br>
                            <label>Report Prepared By</label>
                            <tabs class='ma-0' tabNavClasses="nav-fill flex-column flex-sm-row">
                                <tab-pane title="EBSC staff"></tab-pane>
                                <tab-pane title="Paracounsellor"></tab-pane>
                            </tabs>
                            <base-input label="Rank/Name"></base-input>
                            <base-input label="Signature"></base-input>
                            <base-input label="Date of Report"><date-pickers></date-pickers></base-input>
                        </div> -->

                        <h5 class="heading-title text-warning mb-0">Summary</h5><br>
                        <div class="row">
                            <div class="col-lg-6 col-sm-6">
                                <label>Report Prepared By</label>
                                <div class="row justify-content-left">
                                    <base-checkbox style="margin-left:4%; margin-top:10px; margin-bottom:28px" v-model="reportPreparedBy.ebsc">EBSC staff</base-checkbox>
                                    <base-checkbox style="margin-left:25%; margin-top:10px; margin-bottom:28px" v-model="reportPreparedBy.para">Paracounsellor</base-checkbox>
                                </div>
                                <base-input label="Signature"></base-input>
                            </div>
                            <div class="col-lg-6 col-sm-6">
                                <base-input label="Rank/Name"></base-input>
                                <base-input label="Date of Report"><date-pickers></date-pickers></base-input>
                            </div>
                        </div>
                      </form>

                    </div>
                    <div id="editor"></div>
                    <div class="row justify-content-center">
                        <!-- <a href="#">Submit</a> -->
                        <!-- <modals class="row justify-content-center" v-on:click="retrieveData">check</modals> -->
                        <base-button size="sm " type="primary" style = "height:45px; width:105px; margin-top:31px" v-on:click="saveDraft">Save Draft</base-button>
                        <modal :show.sync="saveSuccess" gradient="primary" modal-classes="modal-danger modal-dialog-centered">
                            <div class="py-3 text-center">
                              <i class="ni ni-check-bold ni-3x"></i>
                              <h4 class="heading mt-4">Save Successfully!</h4>
                            </div>

                            <template slot="footer">
                                <base-button type="link"
                                            text-color="white"
                                            class="ml-auto"
                                            @click="saveSuccess = false">
                                    Close window
                                </base-button>
                            </template>
                        </modal>
                        <base-button size="sm " type="primary" style = "height:45px; width:105px; margin-top:31px" v-on:click="submit" id="submit-btn">Submit</base-button>
                        <modal :show.sync="submitSuccess" gradient="primary" modal-classes="modal-danger modal-dialog-centered">
                            <div class="py-3 text-center">
                              <i class="ni ni-check-bold ni-3x"></i>
                              <h4 class="heading mt-4">Submit Successfully!</h4>
                            </div>

                            <template slot="footer">
                                <base-button type="link"
                                            text-color="white"
                                            class="ml-auto"
                                            @click="submitSuccess = false">
                                    Close window
                                </base-button>
                            </template>
                        </modal>
                    </div>
                    <br>
                </card>
            </div>
        </section>
    </div>
</section>
</template> 


<script>
const DatePickers = () => import("./JavascriptComponents/DatePickers");
import Tabs from "@/components/Tabs/Tabs.vue";
import TabPane from "@/components/Tabs/TabPane.vue";
import TabsSection from "./JavascriptComponents/TabsSection";
import Modals from "./JavascriptComponents/Modals";
import VueTimepicker from "vue2-timepicker/src/vue-timepicker.vue";
import BaseNav from "@/components/BaseNav";
import CloseButton from "@/components/CloseButton";
import Card from "../../components/Card.vue";
import html2pdf from 'html2pdf.js';
import { jsPDF } from "jspdf";
import { VueEditor } from "vue2-editor";
import database from '../../firebase';
import Modal from "@/components/Modal.vue";
import { VBTooltip } from "bootstrap-vue/esm/directives/tooltip/tooltip";
import { VBPopover } from "bootstrap-vue/esm/directives/popover/popover";


export default {
    directives: {
        BTooltip: VBTooltip,
        BPopover: VBPopover,
    },
    data() {
        return {
            isAnnex: false,
            isIntent: false,
            isPlans: false,
            isResources: false,
            isPastAttempt: false,
            isMentalHealth: false,
            race: "",
            name: "",
            age: "",
            maritalstatus: "",
            unit: "",
            contact: "",
            enlistment: "",
            ord: "",
            nric: "",
            reasonsForReferral: "",
            obsOfPresentation: "",
            counsellingGoals: "",
            detailsOfSession: "",
            caseConceptualisation: "",
            interventionsProvided: "",
            reasonsForClosure: "",
            session_num: 1,
            content:"",
            modal:false,
            saveSuccess: false,
            retrieveSuccess: false,
            submitSuccess: false,
            sourceOfReferral: {
                self: false,
                imh: false,
                supervisor: false,
                medicalOfficer: false,
                others: false,
                othersInput: "",
                },
            followUpPlans:{
                client:false,
                unit:false,
                medical:false,
                other:false,
            },
            gender:{
                male:false,
                female:false,
            },
            riskLevel:{
                low:false,
                medium:false,
                high:false,
            },
            reportPreparedBy:{
                ebsc:false,
                para:false,
            }
        };
    },
    components: {
        DatePickers,
        TabPane,
        Tabs,
        TabsSection,
        Modals,
        VueTimepicker,
        BaseNav,
        CloseButton,
        Card,
        VueEditor,
        Modal,
    },
  methods: { 
    signOut() {
      this.$router.push("login");
    },
    
    async retrieveData(){
        var input_nric = this.nric;
        const snapshot = database.collection('patients').doc(input_nric).collection('info').get();
        console.log('====== received snapshot =======')

        snapshot.then(
            querySnapshot => {
                console.log('===== inside a snapshot doc ======')
                if (!querySnapshot.empty){
                    querySnapshot.forEach(doc => {
                        const data = doc.data();
                        this.race = data["race"];
                        this.name = data["name"];
                        this.gender = data["gender"];
                        this.maritalstatus = data["maritalStatus"];
                        this.unit = data["unit"];
                        this.contact = data["contactNumber"];
                        this.enlistment = data["enlistmentDate"];
                        this.age = data["age"];
                        this.ord = data["ord"];
                        this.reasonsForReferral = data["reasonsForReferral"];
                        this.sourceOfReferral = data['sourceOfReferral'];
                        this.followUpPlans = data['followUpPlans'];
                        // this.reportPreparedBy = data['reportPreparedBy'];
                        this.retrieveSuccess = true;
                    })}
                    else {
                        alert("Please check input NRIC again")
                    }
                })
        
    },
    curren_time() {
        const current = new Date();
        const minute = current.getMinutes() < 9 ? "0" + current.getMinutes() : current.getMinutes();
        const hour = current.getHours() < 9 ? "0" + current.getHours() : current.getHours();
        const time = hour + ":" + minute;
        return time;
    },
    clearFields() {
        this.race = "";
        this.name = "";
        this.maritalstatus = "";
        this.unit = "";
        this.contact = "";
        this.enlistment = "";
        this.age = "";
        this.ord = "";
        this.nric = "";
        this.reasonsForReferral= "";
        this.obsOfPresentation= "";
        this.counsellingGoals= "";
        this.detailsOfSession= "";
        this.caseConceptualisation= "";
        this.interventionsProvided= "";
        this.reasonsForClosure= "";
        this.sourceOfReferral= {
            self: false,
            imh: false,
            supervisor: false,
            medicalOfficer: false,
            others: false,
            othersInput: "",
            };
        this.modal = false;
    },
    extractContent(s) {
        var span = document.createElement('span');
        span.innerHTML = s;
        return span.textContent || span.innerText;
    },
    checkOpen(s) {
        // if reasons for closure box is empty, case is still open
        if (s == "") {
            status = true;
        } else {
            status = false;
        }
        return status
    },

    saveInfo() {
        const self = this;
        var nric = document.getElementById("nric").value;

        database
            .collection("patients")
            .doc(this.nric)
            .collection("info")
            .doc("info")
            .set({
            race: this.race,
            name: this.name,
            gender: this.gender,
            maritalStatus: this.maritalstatus,
            unit: this.unit,
            contactNumber: this.contact,
            enlistmentDate: this.enlistment, 
            age: this.age,
            ord: this.ord, 
            reasonsForReferral: this.reasonsForReferral,
            sourceOfReferral: this.sourceOfReferral,
            followUpPlans: this.followUpPlans
        })

        database
            .collection("forms")
            .doc()
            .set({
                name: this.name,
                session_num: 1,
                nric: this.nric,
                reasonsForClosure: this.reasonsForClosure
            })
    },

    saveDraft() {
        const self = this;
        const session_num = this.session_num;
        var nric = document.getElementById("nric").value;

        this.saveInfo();

        database
            .collection("patients")
            .doc(this.nric)
            .collection("forms")
            .doc(session_num.toString())
            .set({
            // sessionNum: this.session_num,
            // reasonsForReferral: this.extractContent(this.reasonsForReferral),
            // obsOfPresentation: this.extractContent(this.obsOfPresentation),
            // counsellingGoals: this.extractContent(this.counsellingGoals),
            // detailsOfSession: this.extractContent(this.detailsOfSession),
            // caseConceptualisation: this.extractContent(this.caseConceptualisation),
            // interventionsProvided: this.extractContent(this.interventionsProvided),

            reasonsForReferral: this.reasonsForReferral,
            obsOfPresentation: this.obsOfPresentation,
            counsellingGoals: this.counsellingGoals,
            detailsOfSession: this.detailsOfSession,
            caseConceptualisation: this.caseConceptualisation,
            interventionsProvided: this.interventionsProvided,

            verbaliseIntent: document.getElementById("verbal-intent").value,
            ambivalenceIntent: document.getElementById("ambivalence-intent").value,
            explorePlans: document.getElementById("explore-plans").value,
            concretePlans: document.getElementById("concrete-plans").value,
            lethalMeans: document.getElementById("lethal-means").value,
            socialResource: document.getElementById("social-resource").value,
            skillsResource: document.getElementById("skills-resource").value,
            suicideAttempt: document.getElementById("suicide-attempt").value,
            mentalHealth: document.getElementById("mental-health").value,
            reasonsForClosure: this.extractContent(this.reasonsForClosure),
            isOpen: this.checkOpen(this.reasonsForClosure),
            sourceOfReferral: this.extractContent(this.sourceOfReferral),
            reportPreparedBy: this.reportPreparedBy,
        })
        .then(function (docRef) {
            console.log("First Session Draft Successfully Saved");
            self.saveSuccess = true
        })
        .catch(function (error) {
            console.error("Error Saving Draft: ", error);
        });
    },
    submit: function () {
        var filled_form = document.getElementById("first-session");
        var draft = false;
        var options = {
            jsPDF: {
            format: "a4",
            },
            html2canvas: { letterRendering: true, useCORS: true, logging: true },
            margin: 2,
            image: { type: "jpeg", quality: 1 },
        };
        var file_name = this.nric + "_" + this.session_num.toString() + ".pdf";
        this.saveDraft();
        html2pdf().set(options).from(filled_form).toPdf().save(file_name);
        this.submitSuccess = true;
    },
    
  },
};
</script>
<style>
#outer {
  width: 100%;
  text-align: center;
}
.inner {
  display: inline-block;
}
</style>

