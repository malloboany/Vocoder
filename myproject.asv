function varargout = myproject(varargin)

% MYPROJECT M-file for myproject.fig
%      MYPROJECT, by itself, creates a new MYPROJECT or raises the existing
%      singleton*.
%
%      H = MYPROJECT returns the handle to a new MYPROJECT or the handle to
%      the existing singleton*.
%
%      MYPROJECT('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in MYPROJECT.M with the given input arguments.
%
%      MYPROJECT('Property','Value',...) creates a new MYPROJECT or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before myproject_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to myproject_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help myproject

% Last Modified by GUIDE v2.5 23-May-2015 19:27:17

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @myproject_OpeningFcn, ...
                   'gui_OutputFcn',  @myproject_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT

% --- Executes just before myproject is made visible.
function myproject_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to myproject (see VARARGIN)

% Choose default command line output for myproject
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes myproject wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = myproject_OutputFcn(hObject, eventdata, handles)
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;

% --- Executes on button press in pushbutton1.
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
set(handles.axes1,'visible','on');
set(handles.text3,'visible','on');

axes(handles.axes1);
cla;


FilterSpec='*.wav';
global myfile mypath;
[myfile,mypath,index] = uigetfile(FilterSpec);
path=strcat(mypath,myfile);

[y1,Fs1] = wavread(path);

%guidata(hObject,handles.y1);

plot(y1);




% --------------------------------------------------------------------
function FileMenu_Callback(hObject, eventdata, handles)
% hObject    handle to FileMenu (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


% --------------------------------------------------------------------
function OpenMenuItem_Callback(hObject, eventdata, handles)
% hObject    handle to OpenMenuItem (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
file = uigetfile('*.fig');
if ~isequal(file, 0)
    open(file);
end

% --------------------------------------------------------------------
function PrintMenuItem_Callback(hObject, eventdata, handles)
% hObject    handle to PrintMenuItem (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
printdlg(handles.figure1)

% --------------------------------------------------------------------
function CloseMenuItem_Callback(hObject, eventdata, handles)
% hObject    handle to CloseMenuItem (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
selection = questdlg(['Close ' get(handles.figure1,'Name') '?'],...
                     ['Close ' get(handles.figure1,'Name') '...'],...
                     'Yes','No','Yes');
if strcmp(selection,'No')
    return;
end

delete(handles.figure1)


% --- Executes on selection change in popupmenu1.
% hObject    handle to popupmenu1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = get(hObject,'String') returns popupmenu1 contents as cell array
%        contents{get(hObject,'Value')} returns selected item from
%        popupmenu1


% --- Executes on button press in pushbutton4.
function pushbutton4_Callback(hObject, eventdata, handles)
set(handles.axes2,'visible','on');
set(handles.text4,'visible','on');
axes(handles.axes2);
cla;
FilterSpec='*.wav';
global myfile2 mypath2; 
[myfile2,mypath2,index] = uigetfile(FilterSpec);
path=strcat(mypath2,myfile2);
[y2,Fs2] = wavread(path);
%handles.y2=y2;
%guidata(hobject,handles);
plot(y2);
% hObject    handle to pushbutton4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


% --- Executes on button press in pushbutton5.
function pushbutton5_Callback(hObject, eventdata, handles)
set(handles.axes3,'visible','on');
set(handles.text7,'visible','on');
axes(handles.axes3);
cla;

global myfile mypath;
global myfile2 mypath2;
path=strcat(mypath,myfile);
path2=strcat(mypath2,myfile2);

chan=str2double(get(handles.chan,'String'));% chan = number of channels  
numband=str2double(get(handles.num,'String'));% numband = number of bands (<chan)

%
% The Channel Vocoder modulates the carrier signal with the modulation signal
modfile          = path2;
carfile            = path;

outputfile       = 'C:\Users\Mohammed\Desktop\output.wav';
[modul,sr1]    =wavread(modfile);
[carrier,sr2]    =wavread(carfile);

                                                 
                                                        
overlap          = .2;                                                     % overlap = window overlap          

[rc, cc]          = size(carrier); 
[rm, cm]        = size(modul);
st                  = min(rc,cc);                                        % stereo or mono?

len                = min(length(carrier),length(modul));      % find shortest length
carrier           = carrier(1:len,1:st);                              % shorten carrier if needed
modul           = modul(1:len,1:st);                               % shorten modulator if needed
L                  = 2*chan;                                             % window length/FFT length
bands           = 1:round(chan/numband):chan;             % indices for frequency bands     
bands(end)   = chan;
y                  = zeros(len,st);                                      % output vector
ii                  = 0;

while ii*L*overlap+L <= len
    ind         = round([1+ii*L*overlap:ii*L*overlap+L]);
    FFTmod  = fft( modul(ind,:) );                                % window & take FFT of modulator
    FFTcar    = fft( carrier(ind,:));                                 % window & take FFT of carrier  
    syn         = zeros(chan,st);                                     % place for synthesized output
    for jj = 1:numband-1                                             % for each frequency band
        b          = [bands(jj):bands(jj+1)-1];                   % current band
        syn(b,:) = FFTcar(b,:)*diag(mean(abs(FFTmod(b,:))));
    end                                   % take product of spectra
    midval    = FFTmod(1+L/2,:).*FFTcar(1+L/2,:);       % midpoint is special
    synfull    = [syn; midval; flipud( conj( syn(2:end,:) ) );]; % + and - frequencies
    timsig     = real( ifft(synfull) );                               % invert back to time
    y(ind,:)   = y(ind,:) + timsig;                                 % add back into time waveform   
    ii            = ii+1;
end

y                = 0.8*y/max(max(abs(y)));                     % normalize output

wavwrite(y,sr1,16,outputfile); % write wave file
plot(y);

% hObject    handle to pushbutton5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


% --- Executes on button press in play1.
function play1_Callback(hObject, eventdata, handles)
% hObject    handle to play1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
global myfile mypath;
path=strcat(mypath,myfile);
[y1,Fs1]=wavread(path);
wavplay(y1,Fs1);


% --- Executes on button press in play2.
function play2_Callback(hObject, eventdata, handles)
global myfile2 mypath2;
path=strcat(mypath2,myfile2);
[y2,Fs2]=wavread(path);
wavplay(y2,Fs2);
% hObject    handle to play2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)


% --- Executes on button press in play_output.
function play_output_Callback(hObject, eventdata, handles)
[y,Fs]=wavread('C:\Users\Mohammed\Desktop\output.wav');
wavplay(y,Fs);
% hObject    handle to play_output (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



function chan_Callback(hObject, eventdata, handles)
% hObject    handle to chan (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of chan as text
%        str2double(get(hObject,'String')) returns contents of chan as a double


% --- Executes during object creation, after setting all properties.
function chan_CreateFcn(hObject, eventdata, handles)
% hObject    handle to chan (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function num_Callback(hObject, eventdata, handles)
% hObject    handle to num (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of num as text
%        str2double(get(hObject,'String')) returns contents of num as a double


% --- Executes during object creation, after setting all properties.
function num_CreateFcn(hObject, eventdata, handles)
% hObject    handle to num (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in record.


% --- Executes on button press in reset.
function reset_Callback(hObject, eventdata, handles)
set(handles.axes3,'visible','off');
set(handles.text7,'visible','off');
set(handles.axes1,'visible','off');
set(handles.text3,'visible','off');
set(handles.axes2,'visible','off');
set(handles.text4,'visible','off');
axes(handles.axes1);
cla;
axes(handles.axes2);
cla;
axes(handles.axes3);
cla;
set(handles.num,'String','400');
set(handles.chan,'String','512');

% hObject    handle to reset (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
