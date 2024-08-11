# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Quantile Regression Model for Residual Lifetime Using an Induced Smoothing Approach Use qris With (In) R Software
install.packages("qris")
install.packages("survival")
library("qris")
library("survival")
qris = read.csv("https://raw.githubusercontent.com/timbulwidodostp/qris/main/qris/qris.csv",sep = ";")
# Estimation Quantile Regression Model for Residual Lifetime Using an Induced Smoothing Approach Use qris With (In) R Software
fm_1 <- Surv(Time_1, Status_1) ~ X
qris_1 <- qris(fm_1, data = qris, t0 = 1, Q = 0.5, nB = 200, "smooth", "pmb", c(1,1))
summary(qris_1)
qris_2 <- qris(fm_1, data = qris, t0 = 1, Q = 0.5, nB = 200, "nonsmooth", "fmb", "rq")
summary(qris_2)
qris_3 <- qris(fm_1, data = qris, t0 = 1, Q = 0.5, nB = 200, "iterative", "fmb", "rq", control = qris.control(maxit = 20, tol = 1e-3, trace = TRUE))
summary(qris_3)
fm_2 <- Surv(Time_2, Status_2) ~ Age + Sex
qris_4 <- qris(fm_2, data = qris, t0 = 0, Q = 0.5, nB = 200, "iterative", "pmb", "rq")
summary(qris_4)
qris_5 <- qris(fm_2, data = qris, t0 = 30, Q = 0.5, nB = 200, "nonsmooth", "fmb", c(1, 0, 1))
summary(qris_5)
qris_6 <- qris(fm_2, data = qris, t0 = 100, Q = 0.5, nB = 200,"smooth", "pmb", "rq")
summary(qris_6)
# Quantile Regression Model for Residual Lifetime Using an Induced Smoothing Approach Use qris With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished