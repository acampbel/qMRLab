noise_level :  Noise histogram fitting within a noise mask
==========================================================

.. raw:: html

   
   <style type="text/css">
   .content { font-size:1.0em; line-height:140%; padding: 20px; }
   .content p { padding:0px; margin:0px 0px 20px; }
   .content img { padding:0px; margin:0px 0px 20px; border:none; }
   .content p img, pre img, tt img, li img, h1 img, h2 img { margin-bottom:0px; }
   .content ul { padding:0px; margin:0px 0px 20px 23px; list-style:square; }
   .content ul li { padding:0px; margin:0px 0px 7px 0px; }
   .content ul li ul { padding:5px 0px 0px; margin:0px 0px 7px 23px; }
   .content ul li ol li { list-style:decimal; }
   .content ol { padding:0px; margin:0px 0px 20px 0px; list-style:decimal; }
   .content ol li { padding:0px; margin:0px 0px 7px 23px; list-style-type:decimal; }
   .content ol li ol { padding:5px 0px 0px; margin:0px 0px 7px 0px; }
   .content ol li ol li { list-style-type:lower-alpha; }
   .content ol li ul { padding-top:7px; }
   .content ol li ul li { list-style:square; }
   .content pre, code { font-size:11px; }
   .content tt { font-size: 1.0em; }
   .content pre { margin:0px 0px 20px; }
   .content pre.codeinput { padding:10px; border:1px solid #d3d3d3; background:#f7f7f7; overflow-x:scroll}
   .content pre.codeoutput { padding:10px 11px; margin:0px 0px 20px; color:#4c4c4c; white-space: pre-wrap; white-space: -moz-pre-wrap; white-space: -pre-wrap; white-space: -o-pre-wrap; word -wrap: break-word;}
   .content pre.error { color:red; }
   .content @media print { pre.codeinput, pre.codeoutput { word-wrap:break-word; width:100%; } }
   .content span.keyword { color:#0000FF }
   .content span.comment { color:#228B22 }
   .content span.string { color:#A020F0 }
   .content span.untermstring { color:#B20000 }
   .content span.syscmd { color:#B28C00 }
   .content .footer { width:auto; padding:10px 0px; margin:25px 0px 0px; border-top:1px dotted #878787; font-size:0.8em; line-height:140%; font-style:italic; color:#878787; text-align:left; float:none; }
   .content .footer p { margin:0px; }
   .content .footer a { color:#878787; }
   .content .footer a:hover { color:#878787; text-decoration:underline; }
   .content .footer a:visited { color:#878787; }
   .content table th { padding:7px 5px; text-align:left; vertical-align:middle; border: 1px solid #d6d4d4; font-weight:bold; }
   .content table td { padding:7px 5px; text-align:left; vertical-align:top; border:1px solid #d6d4d4; }
   ::-webkit-scrollbar {
       -webkit-appearance: none;
       width: 4px;
       height: 5px;
      }
   
      ::-webkit-scrollbar-thumb {
       border-radius: 5px;
       background-color: rgba(0,0,0,.5);
       -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
      }
   </style><div class="content"><h2 >Contents</h2><div ><ul ><li ><a href="#2">I- DESCRIPTION</a></li><li ><a href="#3">II- MODEL PARAMETERS</a></li><li ><a href="#4">a- create object</a></li><li ><a href="#5">b- modify options</a></li><li ><a href="#6">III- FIT EXPERIMENTAL DATASET</a></li><li ><a href="#7">a- load experimental data</a></li><li ><a href="#8">b- fit dataset</a></li><li ><a href="#9">c- show fitting results</a></li><li ><a href="#10">d- Save results</a></li><li ><a href="#11">V- SIMULATIONS</a></li><li ><a href="#12">a- Single Voxel Curve</a></li><li ><a href="#13">b- Sensitivity Analysis</a></li></ul></div><pre class="codeinput"><span class="comment">% This m-file has been automatically generated using qMRgenBatch(noise_level)</span>
   <span class="comment">% Command Line Interface (CLI) is well-suited for automatization</span>
   <span class="comment">% purposes and Octave.</span>
   <span class="comment">%</span>
   <span class="comment">% Please execute this m-file section by section to get familiar with batch</span>
   <span class="comment">% processing for noise_level on CLI.</span>
   <span class="comment">%</span>
   <span class="comment">% Demo files are downloaded into noise_level_data folder.</span>
   <span class="comment">%</span>
   <span class="comment">% Written by: Agah Karakuzu, 2017</span>
   <span class="comment">% =========================================================================</span>
   </pre><h2 id="2">I- DESCRIPTION</h2><pre class="codeinput">qMRinfo(<span class="string">'noise_level'</span>); <span class="comment">% Describe the model</span>
   </pre><pre class="codeoutput">  noise_level :  Noise histogram fitting within a noise mask
     ASSUMPTIONS:
       (1)Uniform noise distribution. Outputs are scalar : all voxels have
           the same value
    
     Fitted Parameters:
       Non-central Chi Parameters
           Sigma
           eta
           N
    
     Options:
        figure             plot noise histogram fit
     Noise Distribution
        Rician             valid if using one coil OR adaptive combine
        Non-central Chi    valid for multi-coil and parallel imaging (parameter N reprensent the effective number of coils)
    
     Author: Ian Gagnon, 2017
    
     References:
       Please cite the following if you use this module:
         FILL
       In addition to citing the package:
         Cabana J-F, Gu Y, Boudreau M, Levesque IR, Atchia Y, Sled JG, Narayanan S, Arnold DL, Pike GB, Cohen-Adad J, Duval T, Vuong M-T and Stikov N. (2016), Quantitative magnetization transfer imaging made easy with qMTLab: Software for data simulation, analysis, and visualization. Concepts Magn. Reson.. doi: 10.1002/cmr.a.21357
   
       Reference page in Doc Center
          doc noise_level
   
   
   </pre><h2 id="3">II- MODEL PARAMETERS</h2><h2 id="4">a- create object</h2><pre class="codeinput">Model = noise_level;
   </pre><h2 id="5">b- modify options</h2><pre >         |- This section will pop-up the options GUI. Close window to continue.
            |- Octave is not GUI compatible. Modify Model.options directly.</pre><pre class="codeinput">Model = Custom_OptionsGUI(Model); <span class="comment">% You need to close GUI to move on.</span>
   </pre><img src="_static/noise_level_batch_01.png" vspace="5" hspace="5" style="width:569px;height:833px;" alt=""> <h2 id="6">III- FIT EXPERIMENTAL DATASET</h2><h2 id="7">a- load experimental data</h2><pre >         |- noise_level object needs 2 data input(s) to be assigned:
            |-   Data4D
            |-   NoiseMask</pre><pre class="codeinput">data = struct();
   <span class="comment">% Data4D.nii.gz contains [70   70    4  197] data.</span>
   data.Data4D=double(load_nii_data(<span class="string">'noise_level_data/Data4D.nii.gz'</span>));
   <span class="comment">% NoiseMask.nii.gz contains [70  70   4] data.</span>
   data.NoiseMask=double(load_nii_data(<span class="string">'noise_level_data/NoiseMask.nii.gz'</span>));
   </pre><h2 id="8">b- fit dataset</h2><pre >           |- This section will fit data.</pre><pre class="codeinput">FitResults = FitData(data,Model,0);
   </pre><pre class="codeoutput">     N        eta      sigma_g
       1.0000    0.0000    7.8648
   
   ...done
   </pre><img src="_static/noise_level_batch_02.png" vspace="5" hspace="5" style="width:560px;height:420px;" alt=""> <h2 id="9">c- show fitting results</h2><pre >         |- Output map will be displayed.
            |- If available, a graph will be displayed to show fitting in a voxel.</pre><pre class="codeinput">qMRshowOutput(FitResults,data,Model);
   </pre><img src="_static/noise_level_batch_03.png" vspace="5" hspace="5" style="width:560px;height:420px;" alt=""> <h2 id="10">d- Save results</h2><pre >         |-  qMR maps are saved in NIFTI and in a structure FitResults.mat
                 that can be loaded in qMRLab graphical user interface
            |-  Model object stores all the options and protocol.
                 It can be easily shared with collaborators to fit their
                 own data or can be used for simulation.</pre><pre class="codeinput">FitResultsSave_nii(FitResults, <span class="string">'noise_level_data/Data4D.nii.gz'</span>);
   Model.saveObj(<span class="string">'noise_level_Demo.qmrlab.mat'</span>);
   </pre><h2 id="11">V- SIMULATIONS</h2><pre >   |- This section can be executed to run simulations for noise_level.</pre><h2 id="12">a- Single Voxel Curve</h2><pre >         |- Simulates Single Voxel curves:
                 (1) use equation to generate synthetic MRI data
                 (2) add rician noise
                 (3) fit and plot curve</pre><pre class="codeinput"><span class="comment">% Not available for the current model.</span>
   </pre><h2 id="13">b- Sensitivity Analysis</h2><pre >         |-    Simulates sensitivity to fitted parameters:
                   (1) vary fitting parameters from lower (lb) to upper (ub) bound.
                   (2) run Sim_Single_Voxel_Curve Nofruns times
                   (3) Compute mean and std across runs</pre><pre class="codeinput"><span class="comment">% Not available for the current model.</span>
   </pre><p class="footer"><br ><a href="http://www.mathworks.com/products/matlab/">Published with MATLAB R2016b</a><br ></p></div>
